# Docker prostredie: izolácia a menší blast radius

V prvom prompte v našom deme nejde o aplikáciu, ktorú staviame. Ale ide o prostredie, kde agent bude bežať. Teda pripravíme minimálne dev prostredie, v ktorom sa Qwen Code CLI spúšťa v izolovanom kontajneri.

## Prečo v Dockeri

Docker setup tu nerobíme len pre pohodlie. Hlavne pre bezpečnosť a izoláciu.

Keď dáme coding agentovi prístup k shellu, súborom a nástrojom, dávame mu reálnu možnosť meniť systém. Preto nechceme, aby bežal priamo na host systéme s plným prístupom ku všetkému.

Oddelíme tri veci:

1. host systém,
2. Qwen Code prostredie,
3. projekt, ktorého agent práve vytvára.

Host systém je náš reálny počítač. Máme na ňom osobné súbory, SSH kľúče, konfigurácie, tokeny a ďalšie citlivé veci.

Qwen Code prostredie je kontajner. Tam beží agent, jeho CLI nástroje, Python, Node.js a všetko, čo potrebuje na prácu.

Projekt, ktorý agent vytvára, je bind-mountnutý adresár. Agent vidí len tú časť filesystemu, ktorú mu explicitne namapujeme.

Tým znižujeme blast radius. Ak agent spraví zlý command, nemá automaticky prístup k celému host systému. Má prístup iba k izolovanému prostrediu.

## Praktické pravidlo

Agentovi mountujeme len to, čo naozaj potrebuje. Nemountujeme celý home adresár, nemountujeme SSH kľúče a nedávame mu zbytočné secrets. Takto vieme agentovi dať dostatok slobody na prácu, ale stále držíme hranice pod kontrolou.

## Úmyselné konflikty v instrukciách

V demonštrácii pre video dáme agentovi pár protichodných informácií na to, aby sme videli, ako ich rieši:

- V `AGENTS.md` je Python 3.12, ale v user message napíšeme „Python LTS", čo je neexistujúca verzia. Agent to musí vyriešiť.
- Z Qwen settings odstránime premenné prostredia `OPENAI_API_KEY`. Agent má na problém prísť a túto premennú doplniť.

Skutočné prostredie často obsahuje protichodné alebo chýbajúce kúsky. Chceme vidieť, či si toho agent všimne a vyrieši to, alebo len slepo nasleduje zadanie.

## Overenie

Keď agent skončí, neurobíme hneď ďalší prompt. Najprv spravíme `git diff`, pozrieme, či vytvoril iba očakávané súbory, skontrolujeme Docker setup a až potom zmenu commitneme. Ak niečo nesedí, spravíme follow-up prompt s ďalšou špecifikáciou.

## Nastavenie modelu

V deme agent používa lokálny Ollama model. Nastavenie v `~/.qwen/settings.json` vyzerá takto:

```json
{
  "env": { "OPENAI_API_KEY": "ollama" },
  "security": { "auth": { "selectedType": "openai" } },
  "model": { "name": "qwen3.8:27b" },
  "modelProviders": {
    "openai": [
      {
        "id": "qwen3.8:27b",
        "name": "Qwen3.8 27B",
        "baseUrl": "http://10.8.0.3:11434/v1",
        "generationConfig": {
          "contextWindowSize": 262144,
          "timeout": 600000
        }
      }
    ]
  }
}
```

## Prompt pre Docker prostredie

Celý prompt pre tento krok, v takom stave, ako bol v videu daný agentovi:

````text
Create a minimal Docker dev environment for running Qwen Code CLI.

Goal:
- Make it easy to run Qwen Code in an isolated container while bind-mounting the current project directory
- Use the following model settings (~/.qwen/settings.json)

  {
    "env": { "OPENAI_API_KEY": "ollama" },
    "security": { "auth": { "selectedType": "openai" } },
    "model": { "name": "qwen3.8:27b" },
    "modelProviders": {
      "openai": [
        {
          "id": "qwen3.8:27b",
          "name": "Qwen3.8 27B",
          "baseUrl": "http://10.8.0.3:11434/v1",
          "generationConfig": {
            "contextWindowSize": 262144,
            "timeout": 600000
          }
        }
      ]
    }
  }

Requirements:
- Verify current LTS versions for Python and Node.js from official sources or package metadata.
- Use a Python LTS base image.
- Install Node.js LTS inside the image.
- Install `@qwen-code/qwen-code@latest` globally during build. FYI binary is `qwen`.
- Auto-install Python dependencies from `requirements.txt` if the file exists.
- Bind mount the current working directory into the container.
- Make sure the agent autoloads the AGENTS.md file (I put it here in this directory for you)

Deliverables:
- `Dockerfile`
- `docker-compose.yml`
- concisely-written `DEV.md`
- minimal `requirements.txt` if none exists

`DEV.md` must include:
- exact Python and Node.js versions used,
- build command,
- run command,
- how the current directory is shared with the container,
- how to run `qwen` inside the container.

Implementation rules:
- Keep the image reasonably small.
- Avoid unnecessary packages.
- Do not overwrite existing files without first explaining the change.
- Keep the setup simple and demo-friendly.

Verification:
- After creating files, run a syntax/config sanity check where possible.
- Build and test end-to-end:

  ```bash
  docker compose build
  docker compose run qwen sh -c "qwen -p 'say hi' --max-wall-time 120"
  ```
````

Všimnite si štruktúru promptu. Nie je tam iba „sprav Docker". Sú tam: cieľ, požiadavky, deliverables, implementačné pravidlá a verification. Agent tak vie rozdeliť úlohu na časti a každú skontrolovať.
