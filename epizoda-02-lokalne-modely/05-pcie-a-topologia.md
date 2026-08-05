# PCIe a multi-GPU realita

Keď idete do väčších modelov alebo do viacerých GPU, narazíte na ďalší praktický limit: priepustnosť PCIe a celkovú topológiu stroja.

Veľa VRAM samo o sebe nestačí. Ak model alebo jeho časti putujú medzi CPU a GPU alebo medzi viacerými GPU, začne hrať rolu to, cez čo si tie dáta posielajú. Pri väčších modeloch alebo multi-GPU setupoch to vie byť citeľný bottleneck.

## Orientačné priepustnosti

| Prepojenie | Približná priepustnosť |
|---|---:|
| PCIe Gen1 x4  | ~1 GB/s |
| PCIe Gen1 x8  | ~2 GB/s |
| PCIe Gen1 x16 | ~4 GB/s |
| PCIe Gen2 x4  | ~2 GB/s |
| PCIe Gen2 x8  | ~4 GB/s |
| PCIe Gen2 x16 | ~8 GB/s |
| PCIe Gen3 x4  | ~4 GB/s |
| PCIe Gen3 x8  | ~8 GB/s |
| PCIe Gen3 x16 | ~16 GB/s |
| NVLink | typicky ~50–100+ GB/s |

Gen1 až Gen3 označuje generáciu PCIe, teda ako rýchla je jedna linka. x4, x8 a x16 označuje počet PCIe liniek, teda aká široká je cesta pre dáta. NVLink je priame vysokorýchlostné prepojenie medzi GPU, ktoré im umožňuje posúvať si dáta rýchlejšie a efektívnejšie než cez bežné PCIe.

## Na čo sa pozerať pri stavbe stroja

Pri stavbe väčšieho stroja sa pozerajte nielen na to, koľko máte VRAM, ale aj na:

- generáciu PCIe,
- počet liniek a priepustnosť,
- rozloženie slotov,
- topológiu medzi GPU,
- a čo vám vôbec dovolí doska, CPU a kábel.
