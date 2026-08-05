# Epizóda 03: Agentové programovanie

Táto epizóda vysvetľuje koncepty agentového programovania: rozdiel medzi modelom, chatbotom a agentom, agentový cyklus, hranice autonómie a prácu s kontextom. Praktický setup v Qwen Code je v epizóde 04.

Video: [Agentové programovanie: čo je AI coding agent a ako nad ním rozmýšľať](https://www.youtube.com/watch?v=HmE1Ge3QlQM)

## Hlavná myšlienka

AI agent nie je chatbot. Chatbot vám odpovie. Agent vie spraviť plán, pozrieť súbory, upraviť kód, spustiť testy a podľa výsledku pokračovať ďalej.

Pri agentovom programovaní už neriešime len to, čo model napíše. Riešime aj to, čo agent vykoná, aké nástroje môže použiť a ako kontrolujeme výsledok.

## Čo si z epizódy odniesť

1. Agent je vtedy agentom, keď riadi postup práce: plánuje, rozhoduje sa, vykonáva, kontroluje a iteruje.
2. Výstupom agenta nie je kód, ale zmena, ktorá prejde kontrolou (testy, typecheck, lint, build).
3. Tool results sú ground truth. Model môže znieť sebavedomo, ale výsledok nástroja je zdroj pravdy.
4. Agent potrebuje hranice: najmenšie oprávnenia, ktoré potrebuje na aktuálnu úlohu.
5. Kontext nie je nekonečná pamäť. Agentovi dávame správny kontext v správnom čase.

## Súbory v tomto priečinku

- [`01-model-chatbot-agent.md`](./01-model-chatbot-agent.md): rozdiel medzi modelom, chatbotom a agentom, schopnosti agenta a výber modelu.
- [`02-agentovy-cyklus.md`](./02-agentovy-cyklus.md): cyklus plan, act, observe, verify, kritériá úspechu, diff ako dôkaz.
- [`03-hranice-a-autonomia.md`](./03-hranice-a-autonomia.md): blast radius, úrovne autonómie a pravidlá pre potvrdzovanie akcií.
- [`04-kontext.md`](./04-kontext.md): context hygiene, context compression a kam patrí ktorý typ informácie.
- [`05-kedy-agentom-dari.md`](./05-kedy-agentom-dari.md): kde sú agenti silní, kde slabí a aká je rola človeka.
