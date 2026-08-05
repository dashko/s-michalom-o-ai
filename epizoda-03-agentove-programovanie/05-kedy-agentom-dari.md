# Na čo sú agenti dobrí a na čo nie

## Kde sa agentom darí

Agentom sa najlepšie darí tam, kde existuje jasný cieľ, existujúci vzor a možnosť overiť výsledok. Napríklad:

- pridaj testy podľa existujúceho štýlu,
- oprav bug a spusti test,
- prejdi projekt a nájdi použitie konkrétnej funkcie,
- uprav endpoint podľa existujúceho patternu.

## Kde sú slabší

Naopak, agenti sú slabší tam, kde je zadanie nejasné, chýbajú kritériá úspechu alebo ide o veľké architektonické rozhodnutie. Tam má agent skôr pripraviť možnosti a riziká, nie rozhodnúť za nás.

## Rola človeka

Agentové programovanie neznamená, že vývojár zmizne z procesu. Mení sa skôr jeho rola. Namiesto písania každého riadku kódu viac riešime:

1. správne zadanie,
2. hranice úlohy,
3. kontrolu plánu,
4. review výsledku,
5. rozhodnutia, ktoré agent nemá hádať.

Agent môže zrýchliť prácu. Zodpovednosť za zmenu ale stále ostáva na človeku.

## Akého agenta vybrať

Existujú aj iní open-source AI agenti, napríklad Open Code. Dôležité je, ako dobre je model integrovaný s agentovým prostredím, ako dobre vie volať tooly a ako stabilne zvláda celý workflow.

Ak chceme používať čo najmenší a najefektívnejší model, pomáha mať natívne prostredie, teda jednu rodinu modelu a agenta. Napríklad:

- Qwen model + Qwen Code,
- Claude Opus + Claude Code,
- GPT + OpenAI Codex.

Platí praktické pravidlo: čím lepší model, tým lepšie agent funguje.
