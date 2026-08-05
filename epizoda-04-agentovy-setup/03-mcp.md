# MCP: kontrolovaný prístup k nástrojom

Keď agent nemá dostať len návod, ale prístup ku konkrétnemu nástroju alebo externému systému, použijeme MCP.

MCP server môže agentovi sprístupniť napríklad databázu, interné API, Jira, CRM alebo vlastnú službu. Cez protokol vystavíme vlastné nástroje, napríklad cez vlastný MCP server, a model ich potom vie volať. Napríklad:

- dotaz do databázy,
- vytvorenie Jira ticketu.

Výhody:

- väčšia stabilita,
- lepšia kontrola a bezpečnosť,
- väčšia customizácia.

Príklad spolupráce: MCP vytiahne dáta z databázy, reportu alebo CRM. Skill z toho potom urobí artefakt, napríklad PDF, XLSX, PPTX alebo peknú sumarizáciu. Výhoda je, že nástroje vieme volať kontrolovane a oddeliť ich od samotného promptu.

## Docker MCP Toolkit

Docker MCP Toolkit je praktický spôsob, ako pridávať MCP servery bez toho, aby sme každý server inštalovali ručne do systému. Docker spraví izolované prostredie a Qwen Code cez MCP gateway dostane prístup iba k vybraným nástrojom, napríklad memory server, search server, Gmail server alebo SQLite server.

Zoznam dostupných MCP serverov: [hub.docker.com/mcp](https://hub.docker.com/mcp)

V Qwen Code potom nastavíme jeden MCP server, ktorý spúšťa Docker gateway:

```json
{
    "mcpServers": [
        {
            "name": "dockerGateway",
            "command": "docker",
            "args": ["mcp", "gateway", "run"],
            "timeout": 30000
        }
    ]
}
```

Pointa je jednoduchá: agent nedostane priamy prístup ku všetkému, ale iba ku konkrétnym MCP serverom, ktoré naozaj potrebujeme.
