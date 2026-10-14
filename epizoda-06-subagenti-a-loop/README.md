# Epizóda 06: Subagenti a loop engineering

V minulých dieloch sme agentovi nedávali jedno veľké zadanie, ale menšie a overiteľné kroky. A každý krok sme museli riadiť ručne.

V tejto epizóde chcem tento proces automatizovať: subagenti si rozdelia prácu a loop ich nechá bežať v cykloch, kým výsledok nespĺňa stanovené kritériá.

Video: [Subagenti a loop engineering](https://www.youtube.com/watch?v=lbvL2256Xxs)

## Hlavná myšlienka

Jeden agent, ktorý si samoreviewuje vlastnú prácu, má tendenciu ju potvrdiť. Má rovnaké predpoklady a rovnaký smer myslenia, aký mal pri písaní.

Riešením nie je viac promptov, ale špecializácia. Subagenti si rozdelia prácu: jeden napíše, druhý skontroluje. Loop drží cyklus v chode a vracia pripomienky tam, kde sa majú opraviť.

Človek definuje cieľ a hranice. Nemusí babysitovať každý krok.

## Čo si z epizódy odniesť

1. Agent, ktorý si samoreviewuje, má tendenciu riešenie potvrdiť. Rozdelenie na implementátora a reviewera dáva nezávislý pohľad.
2. Každý subagent má špecifickú úlohu, vlastný kontext, často iné nástroje a jasný výstup.
3. Reviewer by mal byť read-only. Nemôže riešenie opraviť, môže len vydať verdict.
4. Loop engineering odstraňuje človeka z opakovaného promptovania, ale nechá ho v rozhodovaní.
5. Výber nástrojov je výber hraníc. Každému subagentovi dáme len tie nástroje, ktoré na jeho úlohu potrebuje.

## Súbory v tomto priečinku

- [`01-problem-oneho-agenta.md`](./01-problem-oneho-agenta.md): prečo samoreview a babysitovanie nie je škálovateľné.
- [`02-subagenti.md`](./02-subagenti.md): čo je subagent a ako sa líšia implementátor, reviewer a orchestrátor.
- [`03-loop-engineering.md`](./03-loop-engineering.md): čo je loop, čo je goal a ako sa líšia.
- [`04-workflow-demo.md`](./04-workflow-demo.md): krok za krokom ako beží celý workflow.
- [`05-nastroje-a-bezpecnost.md`](./05-nastroje-a-bezpecnost.md): prečo read-only review je dôležitý a ako výber nástrojov určuje hranice.
- [`06-vysledok-demo.md`](./06-vysledok-demo.md): výsledok na D3, zhrnutie a čo by sme mohli ďalej rozšíriť.
- [`goal.md`](./goal.md): kompletný goal, ktorý sme zadali orchestrátorovi.
- [`implementator.md`](./implementator.md): definícia subagenta implementátora (system prompt + tools).
- [`reviewer.md`](./reviewer.md): definícia subagenta reviewera.
- [`example_output.md`](./example_output.md): príklad výsledného výstupu (D3 commit).
