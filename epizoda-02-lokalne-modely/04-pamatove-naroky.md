# Orientačné pamäťové nároky

Nasledujúca tabuľka je orientačný odhad pamäťových nárokov pri približne 4-bitovej kvantizácii.

| Veľkosť modelu (parametre) | Minimum RAM/VRAM (≈ 4-bit) | Rezerva na kontext |
|---:|---:|---:|
| 0.5B–1B | ~2 GB | ~3–4 GB |
| 1.5B–3B | ~4 GB | ~6–8 GB |
| 4B–6B | ~6 GB | ~8–12 GB |
| 7B–8B | ~8 GB | ~10–16 GB |
| 9B–12B | ~10–12 GB | ~14–20 GB |
| 13B–14B | ~16 GB | ~20–24 GB |
| 20B–22B | ~20–24 GB | ~28–36 GB |
| 30B–34B | ~28–36 GB | ~40–48 GB |
| 40B–45B | ~40–48 GB | ~56–72 GB |
| 65B–70B | ~64–80 GB | ~96–120 GB |
| 100B–120B | ~100–140 GB | ~160–220 GB |

Túto tabuľku berte ako orientačný odhad. Pointa nie je len dostať model do pamäte, ale mať aj rezervu na normálne používanie. Najlepšie je trial-and-error.

## Čo čakať od jednotlivých tried

Pri modeloch vo veľkosti 7 až 8 miliárd parametrov môžete očakávať rýchleho lokálneho asistenta: jednoduchšiu sumarizáciu, základnú prácu s textom alebo ľahšie coding úlohy.

Trieda 13B až 14B je už univerzálnejší model pre bežnú analytickú prácu a rozumnejšiu kvalitu výstupu.

32-miliardová trieda umožňuje serióznejšiu úroveň na náročnejšie úlohy, lepší coding a menšiu chybovosť.

Pri veľkosti 70 miliárd parametrov a viac dostávate maximum z lokálu, ale za cenu veľkého hardvéru a viacerých GPU.
