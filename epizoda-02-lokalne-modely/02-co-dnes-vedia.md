# Sú lokálne modely už dosť dobré?

Ak ste skúšali lokálne modely pred rokmi, možno ste mali pocit, že sú citeľne slabšie než top API modely. Dnes je situácia iná.

Existujú open-weight modely, ktoré sa v náročných benchmarkoch dostávajú na úroveň, ktorá je pre veľa praktických úloh normálne použiteľná. Jedným z príkladov je GPQA, náročný benchmark, ktorý testuje skôr hlbšie porozumenie než povrchné memorovanie.

Dôležitejší než konkrétne číslo je trend: open-weight modely už dnes nie sú len experiment. V benchmarku GPQA Diamond sa medzi poprednými modelmi objavujú aj open-weight modely, napríklad Qwen3.5.

Zdroj grafu: [artificialanalysis.ai, GPQA Diamond](https://artificialanalysis.ai/evaluations/gpqa-diamond)

Top closed modely majú stále navrch v najťažších úlohách, v top reasoningu alebo v špičkovej multimodalite. Starý kompromis „buď kvalita cez API, alebo súkromie cez lokál" ale už neplatí tak jednoznačne, pretože kvalita je dnes aj na lokále.

## Čo s lokálnym modelom spravíte v praxi

Dôležitejšia než benchmark je otázka, čo s modelom reálne viete robiť. Dnes už lokálne modely zvládajú napríklad:

1. sumarizáciu dokumentov alebo extrakciu kľúčových informácií,
2. prácu nad internou knowledge base alebo RAG systémom,
3. pomoc pri programovaní,
4. návrhy opráv, refaktoring alebo code review,
5. opakovaný pracovný cyklus: napíšem, spustím, otestujem, opravím.

Veľmi praktické je to v situáciách, keď:

- nechcete internú dokumentáciu posielať do externého API,
- chcete lokálne analyzovať zmluvy, tickety alebo technické reporty,
- chcete mať coding asistenta priamo vo vlastnom prostredí.

Stále platí, že menšie modely robia viac chýb, kvalita závisí od konkrétneho modelu a top closed modely sú v najťažších úlohách stále lepšie. Rozdiel už ale nie je taký dramatický, aby lokál nedával zmysel.
