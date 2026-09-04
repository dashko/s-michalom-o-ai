# AI agenti prakticky a bezpečne

Tento repozitár obsahuje sprievodné materiály k video sérii od spoločnosti MSG o práci s AI modelmi a AI agentmi.

Cieľom série je ukázať, ako AI agentov a nástroje okolo veľkých jazykových modelov používať prakticky, ale zároveň s rozumnou mierou kontroly, bezpečnosti a rešpektom k súkromiu dát.

V repozitári nájdete príklady promptov, šablóny, poznámky a doplnkové materiály k jednotlivým epizódam.

## Epizódy

### 0. Úvod do série

Úvodná epizóda vysvetľuje, prečo pri AI agentoch neriešime iba odpovede modelu, ale aj to, čo agent môže vykonať. Predstavuje hlavné témy série: limity modelov, súkromie, bezpečnosť a rozdiel medzi vibe codingom a agentovým programovaním.

- Video: [Úvod do série](https://www.youtube.com/watch?v=0YwQXoS6Kpw)
- Materiály: [epizoda-00-uvod/](./epizoda-00-uvod/)

### 1. Ako písať lepšie prompty

Prvá praktická epizóda vysvetľuje základy prompt engineeringu: prečo dobrý prompt nie je iba otázka, ale skôr krátka špecifikácia. Ukazuje rozdiel medzi slabým, zamotaným a dobre štruktúrovaným promptom a obsahuje praktické tipy, ako z modelov dostať lepšie odpovede.

- Video: [Ako písať lepšie prompty](https://www.youtube.com/watch?v=mhM740BVjI0)
- Materiály: [epizoda-01-prompt-engineering/](./epizoda-01-prompt-engineering/)

### 2. Lokálne modely vs API

Druhá epizóda porovnáva lokálne open-weight modely s modelmi cez API. Ukazuje, čo dnes lokálne modely reálne vedia, aký hardvér na ne treba, ako vyzerá reálny multi-GPU build so štyrmi RTX 3090 a kedy sa lokál oplatí viac než API.

- Video: [Lokálne AI modely vs API](https://www.youtube.com/watch?v=iY2mKAOK2n8)
- Materiály: [epizoda-02-lokalne-modely/](./epizoda-02-lokalne-modely/)

### 3. Agentové programovanie

Tretia epizóda vysvetľuje, čo je AI coding agent a ako sa líši od chatbotu. Pokrýva agentový cyklus, kritériá úspechu, hranice a autonómiu agenta a prácu s kontextom.

- Video: [Agentové programovanie: čo je AI coding agent a ako nad ním rozmýšľať](https://www.youtube.com/watch?v=HmE1Ge3QlQM)
- Materiály: [epizoda-03-agentove-programovanie/](./epizoda-03-agentove-programovanie/)

### 4. Praktický setup coding agenta

Štvrtá epizóda ukazuje konkrétny setup v Qwen Code: AGENTS.md, skills, MCP servery, napojenie lokálneho modelu cez Ollama a bezpečnostné guardrails.

- Video: [Praktický setup coding agenta](https://www.youtube.com/watch?v=HllulrejHyI)
- Materiály: [epizoda-04-agentovy-setup/](./epizoda-04-agentovy-setup/)

### 5. Praktické demo: agentový workflow od promptu po commit

Piata epizóda ukazuje agentové programovanie v praxi na demo projekte. Qwen Code postupne postaví nástroj na generovanie commit messages cez MCP, Ollamu, SQLite, FastAPI, React UI a testy. Pointa je riadiť agenta malými, overiteľnými krokmi: prompt, diff, test, review a commit.

- Video: [Praktické demo: agentový workflow od promptu po commit](https://www.youtube.com/watch?v=KeRwi4_Tza4)
- Materiály: [epizoda-05-agentove-demo/](./epizoda-05-agentove-demo/)

## Ako používať tento repozitár

1. Otvorte si priečinok konkrétnej epizódy.
2. Prečítajte si jej `README.md`. Nájdete tam hlavné myšlienky epizódy a zoznam všetkých súborov.
3. Materiály majú rôznu podobu podľa témy epizódy: príklady promptov a šablóny, orientačné tabuľky alebo ukážky konfigurácií (AGENTS.md, settings.json, Modelfile).
4. Príklady promptov si skopírujte do svojho AI nástroja, ukážky konfigurácií si upravte podľa vlastného projektu.
5. Pri experimentovaní meňte vždy iba jednu vec naraz a porovnajte výsledky.

## Témy série

Séria postupne pokryje napríklad:

- prompt engineering,
- lokálne modely,
- agentové programovanie,
- MCP server,
- PydanticAI vrstvu,
- RAG,
- tréningové dáta,
- fine-tuning.

## Poznámka k bezpečnosti

Pri AI agentoch neriešime iba to, čo model odpovie, ale aj to, čo môže vykonať. Preto sa v sérii opakovane vraciame k témam ako obmedzené oprávnenia, kontrolované nástroje, validácia vstupov, auditovateľnosť a súkromie dát.

## Autor

**Michal Bystricky** ([LinkedIn](https://www.linkedin.com/in/dev-michal/)) je dátový vedec v spoločnosti [msg](https://msg-life.sk/), kde sa venuje enterprise AI produktom. Zároveň je zakladateľom [Sharpscale](https://sharpscale.io/sk), jeho konzultačnej a softvérovej spoločnosti, kde prototypuje AI produkty, experimentuje s novými spôsobmi budovania softvéru a skúma, ako môžu AI agenti spolupracovať s ľudskými vývojármi.

