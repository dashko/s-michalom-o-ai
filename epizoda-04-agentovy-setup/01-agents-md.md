# AGENTS.md: README pre AI agentov

AGENTS.md je „README pre AI coding agentov". Dáva agentovi stabilné projektové pravidlá: ako sa spúšťajú testy, aký je coding style, čo nemá robiť a ako má overiť výsledok.

Platí: čím menší a jednoduchší AGENTS.md, tým lepšia presnosť. Platí aj opak: čím viac nesúvisiaceho kontextu agent dostane pre konkrétnu úlohu, tým horší výstup môžeme dostať.

Napríklad ak nechceme, aby agent spúšťal integračné testy, nedáme ich do AGENTS.md ako defaultný krok. Jeden agent by mal byť fokusovaný na jednu špecializovanú činnosť a mal by mať v kontexte len to, čo potrebuje pre svoju prácu, nič iné.

## Ako začať

Na začiatok odporúčame vytvoriť AGENTS.md automaticky. Agent sa sám pozrie na projekt a pripraví prvú verziu tohto súboru.

Automaticky vytvorený AGENTS.md býva ukecaný, preto ho treba zjednodušiť a upraviť podľa toho, aké sú praktiky vo vašom projekte.

## Príklad zlého AGENTS.md

Za ukážku zlého AGENTS.md môžeme považovať napríklad tento: [python-django-scalable-web.md](https://github.com/gakeez/agents_md_collection/blob/main/examples/python-django-scalable-web.md)

Jeho problémy:

- žiadne komentáre k štruktúre,
- pomiešané concerns (deployment pravdepodobne nepotrebujeme pri bežnom vývoji),
- code samples sú doménovo špecifické a implementujú nesúvisiaci projekt,
- env variables by mali byť súčasťou dev setupu, nie všeobecná inštrukcia pre model,
- common issues sú často príliš všeobecné.

Takýto AGENTS.md môže fungovať s veľkým modelom, ale s menším modelom sa v ňom agent ľahko stratí.

## Príklad dobrého AGENTS.md

Dobrý AGENTS.md je oveľa kratší a praktickejší. Nemá modelu vysvetľovať celý svet. Má mu povedať len to, čo potrebuje na prácu v tomto projekte.

```text
# Project instructions

- Use Python 3.12.
- Use `pytest` for tests.
- Before finishing Python changes, run the relevant verification commands:
  - formatter, for example `ruff format .` or the formatter used by the project,
  - linter, for example `ruff check .`,
  - type-checker, for example `mypy .`,
  - Python compilation check, for example `python -m compileall .`,
  - tests, for example `pytest`.
- If a verification command is project-specific, first inspect the README, pyproject.toml, Makefile, or CI config.
- Keep changes small and focused.
- Do not add new dependencies unless the user explicitly approves them.
- Follow existing file structure and naming conventions.
- Never commit secrets or `.env` files.
- If the task is ambiguous, ask before editing.
```

Toto je pre agenta oveľa užitočnejšie než dlhý dokument plný všeobecných pravidiel.

## Verification checklist

Dôležité je, aby AGENTS.md obsahoval aj konkrétny verification checklist. Agent nemá len napísať kód, ale má vedieť, ako overiť, že zmena je v poriadku.

Pri Pythone to často znamená:

1. spustiť formatter,
2. spustiť linter,
3. spustiť typecheck,
4. spustiť Python compilation check,
5. a nakoniec testy.

Nie každý projekt používa rovnaké príkazy. Preto má agent najprv pozrieť `pyproject.toml`, `Makefile`, README alebo CI config a až potom spúšťať správne príkazy.

## Čo všetko agent potrebuje vedieť

1. ako spustiť testy,
2. aký štýl má dodržať,
3. aké formatting, linting, typecheck a compile kontroly má spustiť,
4. čo nesmie robiť,
5. a kedy sa má spýtať.

To je všetko. Čím kratší a presnejší AGENTS.md, tým menšia šanca, že sa agent stratí v nepodstatnom kontexte.
