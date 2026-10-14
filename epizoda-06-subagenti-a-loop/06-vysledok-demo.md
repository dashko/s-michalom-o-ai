# Výsledok

V predchádzajúcom dieli sme AI agentovi dali nakódiť nástroj, ktorý z `git diffu` generuje vtipnú commit message a faktické zhrnutie zmeny.

V tejto epizóde sme ten nástroj rozšírili o dve veci:

1. **História zmien.** Agent sa pozrie na predchádzajúce commity zmenených súborov a vysvetlí, ako aktuálna zmena nadväzuje na predchádzajúci kód.
2. **Zmenené časti.** Zistí, ktorých častí aplikácie sa zmena dotkne a čo po nej treba otestovať.

## Demo na D3

Po dokončení úlohy som agentovi ešte dal jeden test.

Na repozitári knižnice D3, teda knižnice na tvorbu grafov, som mu zadal vygenerovať commit message pre jeden refaktorovací commit.

Výstup sa začal vtipnou vetou: **„D3 sa konečne rozchádza s CommonJS."**

Pod ňou aplikácia vysvetlila prechod na ESM, ukázala predchádzajúce commity, oddelila potvrdené dopady od možných a navrhla konkrétne testy po refaktoringu.

Kompletný príklad výstupu nájdete v `example_output.md`.

## Skalovateľnosť

V tomto deme sme mali troch subagentov: implementátora, reviewera a orchestrátora.

V praxi ich môže byť oveľa viac. Ja napríklad pracujem so 48 subagentmi rozdelenými do piatich tímov, v ktorých spolupracujú.

Keď sa rozhodneme, že chceme viac úrovní reviewu, stačí pridať ďalšieho subagentu. Kvalita, security, testy, dokumentácia, každý môže mať svoj.

## Zhrnutie

Subagenti si rozdelia prácu: jeden napíše, druhý skontroluje.

Loop drží cyklus v chode a posiela úlohy agentom, čo majú robiť.

Ja určím cieľ a hranice. Nemusím babysitovať.

K výsledku sa vrátim, keď je hotový. Rozhodnem sa, či ho chcem použiť.

Pravidlo je jednoduché:

**Agent vie, čo má riešiť. Reviewer vie, čo má posúdiť. Cyklus vie, kedy končí.**
