# Epizóda 01: Ako písať lepšie prompty

Táto epizóda je praktický úvod do prompt engineeringu.

Hlavná myšlienka je jednoduchá: dobrý prompt nie je iba otázka. Je to krátka špecifikácia, ktorá modelu vysvetľuje rolu, cieľ, kontext, obmedzenia, očakávaný formát výstupu a vstupné dáta.

Video: doplniť po zverejnení

## Čo si z epizódy odniesť

1. Prompt sa zvyčajne netrafí na prvýkrát. Dobrý prompt sa iteruje.
2. Zložité úlohy nedávame modelu naraz, ale rozbíjame ich na menšie samostatné kroky.
3. Čím menej musí model hádať, tým lepší výstup dostaneme.
4. Pravidlá a vstupné dáta je dobré oddeľovať, najmä pri práci s cudzím alebo nedôveryhodným textom.

## Súbory v tomto priečinku

- [`00-prehlad-modelov.md`](./00-prehlad-modelov.md) – prehľad modelov použitých alebo spomenutých v epizóde.
- [`01-slaby-prompt.md`](./01-slaby-prompt.md) – jednoduchý, ale príliš nejasný prompt z videa.
- [`02-zamotany-prompt.md`](./02-zamotany-prompt.md) – ukážka príliš dlhého a zamotaného promptu, kde je zmiešaných viac úloh naraz.
- [`03-dobry-prompt.md`](./03-dobry-prompt.md) – lepšia, self-contained verzia promptu so zadanou rolou, cieľom, otázkami, štýlom a vstupom.
- [`04-sablona-promptu.md`](./04-sablona-promptu.md) – univerzálna šablóna promptu, ktorú si môžete skopírovať a upraviť.
- [`05-prakticke-tipy.md`](./05-prakticke-tipy.md) – rozpis praktických tipov z epizódy.
- [`06-prompt-injection.md`](./06-prompt-injection.md) – krátka poznámka k prompt injection a oddeľovaniu pravidiel od dát.
- [`07-temperature.md`](./07-temperature.md) – stručné vysvetlenie nastavenia `temperature`.
- [`08-prakticke-tipy-tabulka.md`](./08-prakticke-tipy-tabulka.md) – praktické tipy v tabuľke so slovenskými aj anglickými copy/paste promptmi.

## Odporúčaný spôsob skúšania

1. Najprv skúste slabý prompt.
2. Potom skúste zamotaný prompt a sledujte, ktoré časti zadania model vynechá alebo pomieša.
3. Nakoniec skúste dobrý prompt a porovnajte kvalitu výstupu.
4. Pri úpravách meňte vždy iba jednu väčšiu vec naraz: napríklad rolu, kontext, obmedzenia alebo formát.
