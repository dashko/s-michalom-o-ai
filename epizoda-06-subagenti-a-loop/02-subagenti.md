# Subagenti

Subagent je špecialista s presne vymedzenou úlohou.

Na rozdiel od jedného generického agenta, ktorý robí všetko, má subagent vlastný systémový prompt, vlastný kontext, často iné nástroje a jasný výstup. V našom deme ich mám troch.

## Implementátor

Píše (alebo upravuje) kód. Má nástroje na čítanie aj na zápis a môže spúšťať testy, build a inú verifikáciu. Keď je hotovo, vráti späť handoff do orchestračnej slučky čo spravil.

## Reviewer

Kód nemôže meniť. Má len nástroje na čítanie. Jeho práca je pozrieť sa na riešenie, posúdiť kvalitu podľa checklistu (správnosť, KISS / DRY / YAGNI, spracovanie chýb, testy, pokrytie) a vydať verdict: `PASS` alebo `FAIL`. Ak je `FAIL`, napíše konkrétny zoznam, čo treba zmeniť a prečo.

Toto je kľúčové. Ak by review robil implementátor, potvrdil si vlastnú prácu. Ak ho robí nezávislý reviewer, máme nezávislú kontrolu.

## Orchestrátor

Riadi. Rozhoduje, kto čo dostane a kedy. V našom deme kód nepíše, len riadi. Posiela úlohu implementátorovi, zoberie review od reviewera, a podľa výsledku rozhodne, či cyklus končí, alebo pokračuje.

## Prečo je to dobré

Rozdelenie na špecializovaných subagentov rieši dva problémy naraz.

1. **Nezávislý pohľad.** Reviewer nepozná smer myslenia implementátora. Číta len kód.
2. **Jasná hranica.** Každý subagent vie, čo má robiť, čo nemá robiť a aký výstup má odovzdať.
