# API vs lokál: základný trade-off

Keď dnes firma alebo tím nasadzuje AI, najčastejšie skončí pri API. Je to logické: zaregistrujete sa, pošlete prompt, dostanete odpoveď a nemusíte riešiť GPU, ovládače, deployment ani infraštruktúru.

Pri lokálnych modeloch beží model vo vašom prostredí: na pracovnej stanici, internom serveri alebo vo vlastnej self-hosted infraštruktúre.

Keď v tejto epizóde hovoríme o lokálnych modeloch, máme väčšinou na mysli open-weight modely, teda modely, pri ktorých máte k dispozícii váhy a viete si ich spustiť sami. Pri closed modeloch cez API model beží u poskytovateľa a vy sa k nemu pripájate ako ku službe.

| Čo je dostupné | Open-weight | Closed-weight cez API | Open-source |
|---|---|---|---|
| Váhy modelu | ✅ áno | ❌ nie | ✅ áno |
| Spustenie u seba | ✅ áno | ⚠️ len cez službu poskytovateľa | ✅ áno |
| Kontrola nad dátami | ✅ vysoká | ⚠️ obmedzená podľa poskytovateľa | ✅ vysoká |
| Kód / architektúra | ⚠️ niekedy čiastočne | ❌ nie | ✅ áno |
| Pohodlie použitia | ⚠️ nižšie | ✅ vysoké | ⚠️ nižšie |

## Čo vám dá lokál

- väčšiu kontrolu nad dátami,
- kontrolu nad verziou a prevádzkou modelu,
- možnosť hlbšej integrácie do vlastných procesov,
- pri pravidelnom používaní aj zaujímavú ekonomiku.

## Čo vám dá API

- rýchly štart,
- silné modely,
- minimum starostí s infraštruktúrou.

Jedno nie je automaticky lepšie než druhé. Dôležité je, že dnes už ide o reálny trade-off, nie o vynútenú voľbu.
