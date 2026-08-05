# Praktický test: lokál vs API

Vo videu porovnávame tri zostavy na rovnakej úlohe: menší lokálny model, väčší lokálny model a API model. Sledujeme tri veci:

1. kvalitu výstupu,
2. rýchlosť odpovede,
3. hardvérové nároky (napríklad cez `nvidia-smi`).

## Testovacia úloha

Jednoduchá a realistická úloha:

```text
Zhrň tento dokument, identifikuj hlavné riziká a navrhni tri odporúčania.
```

Táto úloha je dobrá preto, že kombinuje sumarizáciu, analýzu a rozhodovanie. Práve na takýchto úlohách sa dobre ukáže, kde menší model ešte stačí, kde už väčší model pôsobí istejšie a kde má API model stále navrch.

## Hodnotenie kvality: LLM as a Judge

Ako objektívne porovnať kvalitu odpovedí? Odpovede necháme vyhodnotiť väčším modelom. Tento „judge" model dostane pôvodný dokument a všetky odpovede modelov. Jeho úlohou je porovnať ich kvalitu bez ohľadu na to, ktorý model ich vytvoril.

Eval prompt z videa:

```text
Si nezávislý hodnotiteľ (LLM-as-a-Judge).
Hodnoť len textový obsah odpovedí.
Nehodnoť vzhľad, formát screenshotu ani identitu modelov.

Analyzuj priložený screenshot s odpoveďami viacerých LLM modelov.
Každý stĺpec obsahuje jednu odpoveď jedného modelu.
Odpovede čísluj zľava doprava ako Odpoveď 1, Odpoveď 2, Odpoveď 3.

Každú odpoveď ohodnoť na škále 1–5 podľa:
1. presnosti
2. úplnosti
3. štruktúry
4. analytickej hodnoty
5. praktickosti odporúčaní

Výstup vo formáte:
1. tabuľka skóre pre všetky odpovede
2. plusy a mínusy pre každú odpoveď
3. konečné poradie od najlepšej po najslabšiu

Ak nie je niečo zo screenshotu čitateľné alebo isté, stručne to uveď a nehádaj.
```
