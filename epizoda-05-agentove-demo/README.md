# Epizóda 05: Praktické demo: agentový workflow od promptu po commit

V tejto epizóde si ukážeme agentové programovanie v praxi na demo projekte. Nepúšťame agenta na jedno veľké zadanie, ale dávame mu menšie a overiteľné kroky: Docker prostredie, MCP server na generovanie commit messages, SQLite logovanie, API s React UI a Playwright test.

Video: doplniť po zverejnení

## Hlavná myšlienka

Najväčšia chyba pri coding agentoch je pustiť ich na veľkú úlohu bez kontroly. Prompt typu „postav celú aplikáciu" znie lákavo, ale často skončí chaosom: veľa súborov, nejasný diff, padnuté testy a zmeny, ktoré sme nechceli.

Lepší prístup je agentový workflow. Malý prompt, malý krok, kontrola diffu, test, review, commit. Až potom ďalší krok. Agent môže písať rýchlo, ale človek musí často robiť review.

## Čo si z epizódy odniesť

1. Agentový workflow je postup, nie jeden magický prompt.
2. Každá iterácia má skončiť diffom, testom, reviewom a commitom. Commit je checkpoint, ku ktorému sa vieme vrátiť.
3. Qwen Code spúšťame v izolovanom Docker prostredí, aby agent mal menej možností spraviť škodu.
4. Dobrý je malý prompt: cieľ, požiadavky, výstupy a verification.
5. Lokálny model (Qwen 27B na dvoch GPU) zvládne viac-krokové build end-to-end bez akéhokoľvek externého cloudového API.

## Súbory v tomto priečinku

- [`01-agentovy-workflow.md`](./01-agentovy-workflow.md): prečo malý krok, kontrola, commit. Rozdiel agentového programovania a vibe codingu.
- [`02-docker-a-bezpecnost.md`](./02-docker-a-bezpecnost.md): prečo v Dockeri, izolácia, blast radius, úmyselné konflikty v instrukciách. Prompt pre Docker prostredie.
- [`03-mcp-server.md`](./03-mcp-server.md): MCP server s toolom `summarize_git_diff`, Jinja2 šablóna, `.env.example`. Prompt a follow-up prompt.
- [`04-sqlite-logovanie.md`](./04-sqlite-logovanie.md): SQLite logovanie vygenerovaných commit messages, druhý tool na opravu. Schéma tabuľky.
- [`05-api-a-react-ui.md`](./05-api-a-react-ui.md): FastAPI endpointy, React UI, Playwright test.
- [`06-testovanie-llm-as-a-judge.md`](./06-testovanie-llm-as-a-judge.md): ako testovať výstup LLM modelu pomocou druhého LLM volania.
- [`AGENTS.md`](./AGENTS.md): projektový kontext pre agenta, použitý ako ukážka v demo projekte.
