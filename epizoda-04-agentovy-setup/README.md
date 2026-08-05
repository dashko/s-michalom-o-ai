# Epizóda 04: Qwen Code v praxi: AGENTS.md, skills, MCP a lokálny setup

Táto epizóda ukazuje praktický setup pre coding agenta v Qwen Code: AGENTS.md, skills, MCP servery, napojenie lokálneho modelu cez Ollama a bezpečnostné guardrails.

Video: doplniť po zverejnení

## Hlavná myšlienka

Agent bez setupu je ako junior developer bez README. Môže byť šikovný, ale ak nevie, ako projekt funguje, začne hádať: nevie, ako sa spúšťajú testy, nepozná coding style, nepozná hranice a nevie, ktoré príkazy sú bezpečné a ktoré už môžu spraviť škodu.

Preto pri agentoch nestačí mať dobrý model. Potrebujeme aj dobré prostredie: AGENTS.md, skills, MCP, model setup, permission režimy a guardrails.

## Čo si z epizódy odniesť

1. AGENTS.md je README pre AI agentov. Čím je kratší a presnejší, tým lepšie.
2. Skills držia opakovateľné postupy mimo hlavného kontextu. Pri menších modeloch je to obzvlášť dôležité.
3. MCP dáva agentovi kontrolovaný prístup k externým nástrojom a systémom.
4. Approval mode určuje úroveň autonómie, permissions sú technické mantinely. Deny má vždy najvyššiu prioritu.
5. Agentovi dávame najmenšie oprávnenia, ktoré potrebuje na aktuálnu úlohu.

## Súbory v tomto priečinku

- [`01-agents-md.md`](./01-agents-md.md): čo patrí do AGENTS.md, zlý a dobrý príklad, verification checklist.
- [`02-skills.md`](./02-skills.md): skills ako rozšírenie agentových schopností.
- [`03-mcp.md`](./03-mcp.md): MCP servery a Docker MCP Toolkit.
- [`04-ollama-a-model.md`](./04-ollama-a-model.md): nastavenie Ollamy, settings.json pre Qwen Code, read-only fáza.
- [`qwen-coder.Modelfile`](./qwen-coder.Modelfile): Modelfile pre Ollamu použitý vo videu.
- [`05-guardrails.md`](./05-guardrails.md): approval mode, permissions, .qwenignore a filtrovanie MCP toolov.
- [`06-typicke-zlyhania.md`](./06-typicke-zlyhania.md): typické failure modes agentov a kedy agenta zastaviť.
