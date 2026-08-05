# Cena: lokál vs API

Pri API je model jednoduchý: platíte priebežne za používanie, za tokeny. Výhody sú nulový hardvér, rýchly štart a jednoduché škálovanie. Nevýhoda je, že náklad rastie s používaním.

Pri lokále je logika opačná. Hlavný náklad je na začiatku (hardvér) a potom riešite elektrinu, údržbu a správu.

Férové porovnanie má preto dve vrstvy:

1. prevádzkový náklad, napríklad elektrina,
2. celkový náklad, teda hardvér, čas, správa a návratnosť v čase.

Ak sa pozeráte len na samotnú elektrinu, lokál môže vyzerať veľmi lacno. To ale ešte neznamená, že je automaticky lacnejší než API.

## Orientačný prepočet prevádzkových nákladov

| Scenár | Odhad tok/s | Tok/h | €/h lokál (len elektrina) | €/h API gpt-4o-mini | €/h API GPT-4.1 | €/h API Claude Sonnet |
|---|---:|---:|---:|---:|---:|---:|
| 2× RTX 3090 → 7B trieda | 140 | 504,000 | €0.170 | €0.278 | €5.564 | €6.955 |
| 2× RTX 3090 → 13B trieda | 34 | 122,400 | €0.170 | €0.068 | €1.351 | €1.689 |
| 2× RTX 3090 → 32B trieda | 40 | 144,000 | €0.170 | €0.079 | €1.590 | €1.987 |
| 2× RTX 3090 → 70–80B trieda | 18 | 64,800 | €0.170 | €0.036 | €0.716 | €0.894 |
| ASUS Ascent GX10 (len elektrina) | — | — | €0.048 | — | — | — |

Cena elektriny €0.226 / kWh

Tabuľka ukazuje, koľko tokenov miniete pri konkrétnej zostave a ako by vyzerali náklady na elektrinu oproti nákladom na konkrétne API modely. Elektrina pre 2× RTX 3090 vychádza konštantne okolo 0,17 eura za hodinu, API modely sa pohybujú od desiatok centov až po jednotky eur. Najlacnejšia možnosť v tabuľke je ASUS Ascent GX10 za 0,048 eura za hodinu.

## Ako túto tabuľku čítať

Toto nie je porovnanie „koľko stojí rovnaká kvalita výstupu". Je to orientačné porovnanie prevádzkového nákladu pri určitých triedach modelov a určitom type zaťaženia.

Dôvody opatrnosti:

- 7B model nie je ekvivalent GPT-4.1,
- rôzne úlohy majú rôzne tokenové profily,
- výsledok závisí od batchingu, kontextu, pomeru vstup/výstup aj reálneho využitia stroja.

Pointa tabuľky je jednoduchá: ak lokálny hardvér využívate pravidelne, samotná prevádzka nemusí byť drahá. Skutočná výhodnosť ale závisí od toho, ako intenzívne systém používate, akú kvalitu potrebujete a či započítate aj obstarávaciu cenu a čas na správu.
