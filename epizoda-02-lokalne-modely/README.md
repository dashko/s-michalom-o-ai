# Epizóda 02: Lokálne AI modely vs API

Táto epizóda porovnáva lokálne open-weight modely s modelmi dostupnými cez API. Ukazuje, čo dnes lokálne modely reálne vedia, aký hardvér na ne potrebujete a kedy sa oplatia viac než API.

Video: [Lokálne AI modely vs API: kedy sa oplatia, aký treba hardvér a čo dnes reálne vedia](https://www.youtube.com/watch?v=iY2mKAOK2n8)

## Hlavná myšlienka

Pri API kupujete pohodlie. Pri lokále kupujete kontrolu.

Lokálne open-weight modely už nie sú len hračka pre nadšencov. Na veľa reálnych úloh dnes stačia: sumarizácia dokumentov, práca s internými dátami, RAG alebo coding asistent.

## Čo si z epizódy odniesť

1. Kvalita open-weight modelov výrazne narástla. Starý kompromis „buď kvalita cez API, alebo súkromie cez lokál" už neplatí tak jednoznačne.
2. Pri lokálnych modeloch vás najčastejšie limituje VRAM. Rozhoduje veľkosť modelu, miera kvantizácie a rezerva na kontext.
3. Pri viacerých GPU nerozhoduje iba súčet VRAM, ale aj priepustnosť PCIe a topologia stroja.
4. Náklady porovnávajte v dvoch rovinách: samotná prevádzka (elektrina) a celkový náklad vrátane hardvéru, času a správy.
5. Lokál znamená väčšiu kontrolu nad dátami, ale prístupové práva, logging a audit riešite stále.

## Súbory v tomto priečinku

- [`01-api-vs-lokal.md`](./01-api-vs-lokal.md): základný trade-off medzi API a lokálnym nasadením.
- [`02-co-dnes-vedia.md`](./02-co-dnes-vedia.md): kde sa dnes lokálne modely posunuli a čo s nimi reálne spravíte.
- [`03-vram-a-kvantizacia.md`](./03-vram-a-kvantizacia.md): prečo je VRAM hlavný limit a čo robí kvantizácia.
- [`04-pamatove-naroky.md`](./04-pamatove-naroky.md): orientačné pamäťové nároky podľa veľkosti modelu.
- [`05-pcie-a-topologia.md`](./05-pcie-a-topologia.md): priepustnosť PCIe a na čo myslieť pri multi-GPU.
- [`06-build-a-hardware.md`](./06-build-a-hardware.md): reálny build 4× RTX 3090, DIY vs kompaktný AI box a orientačné ceny hardvéru.
- [`07-test-lokal-vs-api.md`](./07-test-lokal-vs-api.md): praktický test na rovnakej úlohe a eval prompt LLM-as-a-Judge.
- [`08-kedy-lokal-kedy-api.md`](./08-kedy-lokal-kedy-api.md): kedy dáva zmysel lokál, kedy API a kedy hybrid.
- [`09-naklady.md`](./09-naklady.md): orientačný prepočet prevádzkových nákladov lokál vs API.
- [`10-lokal-a-sukromie.md`](./10-lokal-a-sukromie.md): prečo lokál automaticky neznamená vyriešenú bezpečnosť.

## Poznámka k číslam

Tabuľky pamäťových nárokov, priepustností a nákladov sú orientačné odhady z videa. Ceny hardvéru aj API modelov sa menia, preto si ich pred vlastným rozhodnutím overte podľa aktuálnej ponuky.
