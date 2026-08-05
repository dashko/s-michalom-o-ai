# Reálny build a dve cesty k lokálnemu AI stroju

## Reálny build: 4× RTX 3090

Vo videu je ukážka reálneho buildu so 4× RTX 3090, teda spolu 96 GB VRAM, s detailnými zábermi na rozloženie kariet, airflow, napájanie a spacing medzi GPU.

Na papieri vyzerá takýto stroj výborne. Realita buildovania je ale oveľa menej romantická než na papieri. Rýchlo začnete riešiť fyzický priestor, chladenie, PCIe rozloženie, napájanie a kabeláž.

Na internete vyzerá 4×3090 ako super nápad. V realite veľmi rýchlo zistíte, že väčší problém než papierový výkon je fyzika.

## Dve realistické cesty

### Cesta 1: DIY GPU build

Klasický počítač alebo workstation s jednou alebo viacerými GPU.

Výhody:

- flexibilita,
- rozšíriteľnosť,
- dobrý ekosystém,
- pri použitých kartách často veľmi zaujímavý pomer výkon/cena.

Nevýhody:

- vyššia spotreba,
- viac tepla a hluku,
- viac starostí so skladaním,
- pri viacerých GPU aj viac mechanických a prevádzkových problémov.

### Cesta 2: kompaktný AI box (napríklad NVIDIA GB10)

Kompaktnejšie zariadenie typu plug-and-play.

Výhody:

- jednoduchší deployment,
- nižšia spotreba,
- menej starostí s buildom.

Nevýhody:

- menšia flexibilita,
- iná architektúra,
- špecifické limity kompatibility,
- niekedy menší výber softvérového stacku alebo rozšíriteľnosti.

## Orientačné obstarávacie náklady

| Položka | DIY (2× RTX 3090) – odhad | ASUS Ascent GX10 |
|---|---:|---:|
| GPU / akcelerátor | 2× RTX 3090 (used) ~ €700/ks → **€1,400** | integrovaný NVIDIA Blackwell (GB10) |
| CPU + doska | **€450** | v cene |
| RAM | **€500** | **128 GB unified** (v cene) |
| SSD | **€150** | 1 TB |
| PSU | **€200** | v cene |
| Case + chladenie | **€200** | v cene |
| Ostatné | **€200** | v cene |
| **Spolu počiatočná investícia** | **≈ €3,300** | **≈ €3,600** |
| Spotreba pri AI load | **~0.85 kW** | **≤ 0.24 kW** |
| Elektrina / hod pri €0.20/kWh | **€0.17/h** | **€0.048/h** |
| Architektúra | x86 / amd64 | arm |
| Reálne modely (kvant) | 7B ✅ / 13B ✅ / 32B ✅ / 70–80B ⚠️ | 7B ✅ / 13B ✅ / 32B ✅ / 70–80B ✅ |

Cena elektriny €0.226 / kWh
