# Hardvér: hlavný limit je VRAM

Ak si máte z technickej časti zapamätať jednu vec, tak túto: pri lokálnych modeloch vás najčastejšie limituje pamäť grafickej karty, teda VRAM.

Čím väčší model používate a čím vyššiu presnosť chcete, tým viac pamäte potrebujete.

## Kvantizácia

Kvantizácia je technika, vďaka ktorej viete model uložiť v nižšej presnosti, napríklad 8-bitové čísla v 4-bitovej forme. Praktický dôsledok je jednoduchý: model sa zmestí do menšej pamäte a viete ho rozbehať aj na hardvéri, na ktorom by sa inak nezmestil.

Za to zvyčajne zaplatíte určitým poklesom kvality. Pri dobre zvolenej kvantizácii býva tento pokles často menší, než by ľudia čakali.

V praxi teda balansujete medzi tromi vecami:

1. veľkosť modelu,
2. kvalita kvantizácie,
3. hardvér, ktorý máte k dispozícii.

## Zlá otázka a lepšia otázka

Nestačí sa pýtať „Zmestí sa to?".

Lepšia otázka je „Zmestí sa to s rezervou tak, aby sa to dalo normálne používať?".

Model, ktorý sa do pamäte nejako natlačí, ešte nemusí byť použiteľný na reálnu prácu. Potrebujete rezervu na kontext a na runtime overhead. Podrobnejší rozpis nárokov je v súbore [`04-pamatove-naroky.md`](./04-pamatove-naroky.md).
