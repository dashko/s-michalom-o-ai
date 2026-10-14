# Loop engineering

Orchestrátor je fajn. Len ho musím stále ručne riadiť.

A tu sa dostávame k ďalšiemu kroku: loop engineering.

## Čo je loop

Loop je cyklus, v ktorom odstraňujeme človeka z opakovaného promptovania.

Agent urobí malý krok. Výsledok sa vyhodnotí. Spätná väzba sa použije ako vstup pre ďalší krok. Cyklus beží, kým výsledok nespĺňa stanovené podmienky, alebo kým nenarazí na limit.

Človek z rozhodovania nevymizne. Stále definuje:

- **cieľ** — čo sa má zrealizovať,
- **pravidlá** — ako sa má zrealizovať,
- **hranice** — čo sa smie spraviť a čo nie,
- **limit** — kedy sa cyklus zastaví.

Až potom sa vráti k výsledku.

## Ako to beží

1. Orchestrátor pošle úlohu implementátorovi.
2. Implementátor upraví kód, spustí testy a kontroly.
3. Orchestrátor pošle diff a výsledky kontrolov review-ér.
4. Reviewer hodnotí `PASS` alebo `FAIL` s konkrétnym zoznamom akcií.
5. Ak je `FAIL`, orchestrátor pošle priamu spätnú väzbu implementátorovi a ideme od začiatku.
6. Ak je `PASS` (alebo narazí na limit), goal sa ukončí.

## Slučka vs. goal

Slučka s počítadlom beží, kým review nesplní `PASS`, alebo kým nenarazí na limit iterácií. To je klasický loop.

Goal je to isté, zabalené do jedného kontextu: cieľ, milestones, pravidlá a podmienky ukončenia. Orchestrátor má jedno miesto, kde číta a jedno miesto, kde píše.

V našom deme používame goal, je to jednoduchšie a je ho ľahšie sledovať.

## Čo tým získame

Človeka odstránime z opakovaného zadávania promptov, nie z rozhodovania.

Ak je úloha zložitejšia, agent môže bežať aj hodiny. Ak je jednoduchá, skončí po pár minútach. V oboch prípadoch sa človek vráti len k výsledku.
