# Guardrails: approval mode a permissions

Guardrails sú mantinely, ktoré agentovi hovoria, čo môže a čo nemôže robiť. V Qwen Code je dôležité rozlíšiť dve veci: approval mode a permissions.

Approval mode hovorí, koľko autonómie agent má. Permissions hovoria, ktoré tooly, súbory alebo príkazy sú povolené, ktoré sa majú vždy pýtať a ktoré sú úplne zakázané.

Čiže approval mode je úroveň autonómie. Permissions sú technické guardrails.

## Príklad nastavenia projektu

Napríklad `auto-edit` znamená, že agent môže automaticky upravovať súbory, ale shell príkazy stále vyžadujú potvrdenie. `yolo` znamená, že agent má oveľa viac voľnosti. Ale aj v autonómnejšom režime vieme cez `permissions.deny` zablokovať konkrétne veci.

V projektovom `.qwen/settings.json` môžeme nastaviť:

```json
{
  "tools": {
    "approvalMode": "auto-edit"
  },
  "permissions": {
    "allow": [
      "Read(/src/**)",
      "Read(/tests/**)",
      "Edit(/src/**)",
      "Edit(/tests/**)",
      "Bash(git status)",
      "Bash(npm run test*)"
    ],
    "ask": [
      "Bash(npm install *)",
      "Bash(git push *)",
      "Bash(docker *)"
    ],
    "deny": [
      "Read(.env)",
      "Read(/secrets/**)",
      "Edit(/.github/**)",
      "Bash(rm -rf *)",
      "Bash(sudo *)",
      "WebFetch"
    ]
  }
}
```

Toto znamená: agent môže čítať a upravovať `src/` a `tests/`, môže spustiť testy a `git status`, ale pri inštalácii balíkov, pushi alebo Docker príkazoch sa musí opýtať. Zároveň nesmie čítať `.env`, nesmie čítať `secrets/`, nesmie meniť `.github/`, nesmie spustiť `rm -rf`, `sudo` ani volať web.

## Poradie pravidiel

Dôležité je poradie: `deny` má vyššiu prioritu než `ask` a `allow`. Ak niečo zakážeme cez `deny`, agent to nemá spraviť ani vtedy, keď je režim voľnejší.

Qwen Code má aj praktickú ochranu proti obchádzaniu cez shell. Ak napríklad zakážeme `Read(.env)`, agent by to nemal obísť cez príkaz typu `cat .env`.

## .qwenignore

Na obmedzenie súborov vieme použiť aj `.qwenignore`. Ten funguje podobne ako `.gitignore` a povie Qwen Code, ktoré súbory alebo adresáre nemá načítavať cez nástroje, ktoré tento ignore rešpektujú.

```text
# .qwenignore
.env
secrets/
private-notes/
*.pem
```

## Filtrovanie toolov pri MCP

Pri MCP serveroch vieme ísť ešte konkrétnejšie. Pri každom MCP serveri môžeme použiť `includeTools` alebo `excludeTools`, teda povoliť iba vybrané tooly z daného servera.

Napríklad ak MCP server ponúka viac databázových nástrojov, môžeme agentovi sprístupniť iba bezpečný read-only tool a zakázať tooly, ktoré menia dáta. Konkrétne názvy toolov závisia od daného MCP servera.

```json
{
  "mcpServers": {
    "database": {
      "command": "docker",
      "args": ["mcp", "gateway", "run"],
      "includeTools": ["query"],
      "excludeTools": ["execute", "drop_table"]
    }
  }
}
```

Týmto agentovi nedávame iba odporúčanie. Dávame mu technické hranice priamo v Qwen Code. Textové pravidlo hovorí agentovi, čo by mal robiť. Permission pravidlo hovorí prostrediu, čo agent reálne môže spraviť.
