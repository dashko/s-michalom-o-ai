# Workflow demo: od goalu po verdict

Poďme to rozobrať na konkrétne kroky. V našom deme kódime rozšírenie z predchádzajúceho nástroja, ktorý z `git diffu` generoval vtipnú commit message a faktické zhrnutie zmeny.

Teraz pridáme dve veci:

1. **História zmien.** Agent sa pozrie na predchádzajúce commity zmenených súborov a vysvetlí, ako aktuálna zmena nadväzuje na predchádzajúci kód.
2. **Zmenené časti.** Zistí, ktorých častí aplikácie sa zmena dotkne a čo po nej treba otestovať.

## Kedy sa to začne

Ja zadam cieľ (goal): čo sa má zrealizovať a aké pravidlá sa majú dodržať. Dám aj milestones: ako rozpoznať, že je milestone hotový, a aké kritériá má spĺňať.

Keď orchestrátor dostane goal, vie, čo má robiť a podľa čoho rozhodovať, kedy končí.

## Kroky

1. **Ja zadam cieľ a hranice.**
2. **Orchestrátor pošle úlohu implementátorovi.** Dá mu celý kontext: cieľ, relevantný kód, aktuálny stav.
3. **Implementátor píše (alebo upravuje) kód a spúšťa kontroly.** Format, lint, type check, testy. Vracia diff a výsledky.
4. **Orchestrátor pošle diff a výsledky review-érovi.** Reviewér číta kód, posúdi kvalitu, overí princípy, testy, pokrytie.
5. **Review hodnotí `PASS` alebo `FAIL`.**
6. **Ak je `FAIL`,** orchestrátor pošle pripomienky implementátorovi a cyklus pokračuje. Ak je `PASS` alebo narazíme na limit, goal sa ukončí.

## Čo to znamená v praxi

V takomto cykle vieme opakovane kontrolovať kvalitu návrhu a kódu.

Namiesto pár minút môžu agenti pracovať na jednej úlohe aj niekoľko hodín. V našom prípade pracovali približne štyri hodiny.

Môj čas boli hlavne tie úvodné minúty, keď som definoval goal, a tie minúty na konci, keď som výsledok skontroloval. Nemusel som sedieť pri chate, kontrolovať každý krok a vymýšľať ďalší prompt.

Ak potrebujem riešiť aj ďalšie veci, môžem pridať subagentov, ktorí osobitne preveria logovanie, výkon, bezpečnosť, testy alebo dokumentáciu. Pre každú vlastnosť môže byť ďalšia overovacia fáza.
