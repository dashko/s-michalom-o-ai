# MCP server: sumarizácia git diff

V čistom Docker prostredí ďalej pokračujeme. Pôvodne inštalovaný Qwen Code použijeme a postavíme slúbený MCP server.

Agent vytvorí Python MCP server s jedným toolom `summarize_git_diff`. Tool zoberie git diff, voliteľný kontext, zavolá Ollamu a vráti commit message.

## Štruktúra promptu

Dobrý prompt tu rozdelí úlohu na časti:

1. MCP server,
2. konfigurácia cez `.env`,
3. Jinja2 prompt template,
4. volanie Ollamy cez `httpx`,
5. jeden happy-path test.

Toto funguje preto, že agent nerieši všetko naraz ako chaos. Má jasnú štruktúru a vie si kontrolovať jednotlivé kroky.

Vo videu si všimnite, že agent počas programovania vyriešil inštaláciu chýbajúcich balíkov a závislosti sám.

## Jinja2 šablóna

Šablóna je mimo Python kódu, v súbore `templates/commit_summary.j2`:

```text
Act as a cleverly funny developer.

Provide:
1. A one-sentence humorous headline starting with one of: [fix], [feat], [docs], [refactor], [test]
2. A concise technical summary of the actual code changes.

Use the context only to understand intent.
Do not invent changes that are not visible in the diff.

--- GIT DIFF ---
{{ git_diff_output }}

--- OTHER CONTEXT ---
{{ other_context }}
```

Prompt nemáme v kóde, ale v súbore - šablóne, kde ho vieme samostatne upravovať a testovať.

## `.env.example`

Pre konfiguráciu na runtime agent používa `.env` + `python-dotenv` a vytvorí `.env.example`:

```text
OLLAMA_URL="http://10.8.0.3:11434/v1"
MODEL="qwen3.8:27b"
```

Ak vytvorí reálny `.env` na lokálne testy, hodnoty majú byť jasne falošné alebo len placeholder.

## Prompt pre MCP server

Celý prompt, v takom stave, ako bol v videu daný agentovi:

```text
Build a small Python project that exposes an MCP HTTP server for generating commit-message summaries from git diffs.

1) MCP Server

Create an MCP HTTP server using `mcp.server.fastmcp`.

Requirements:
- Put the server and tool implementation in `server.py`.
- Use transport `streamable-http`.
- Run on port `8042`.
- Expose one tool:

    summarize_git_diff(git_diff_output: str, other_context: str = "")

The tool should:
- render a prompt from a Jinja2 template,
- call Ollama using `httpx`,
- return a short humorous headline plus a concise technical summary.


Configuration:
- Use `.env` + `python-dotenv`.
- Do not hardcode runtime configuration in Python code.
- Create `.env.example` for runtime configuration examples with:

    OLLAMA_URL="http://10.8.0.3:11434/v1"
    MODEL="qwen3.8:27b"

- If you create a real `.env` for local demo purposes, keep values clearly fake or placeholder.

Prompt template:
- Do not inline the prompt in Python code.
- Store it in `templates/commit_summary.j2`.
- Template should include:

    Act as a cleverly funny developer.

    Provide:
    1. A one-sentence humorous headline starting with one of: [fix], [feat], [docs], [refactor], [test]
    2. A concise technical summary of the actual code changes.

    Use the context only to understand intent.
    Do not invent changes that are not visible in the diff.

    --- GIT DIFF ---
    {{ git_diff_output }}

    --- OTHER CONTEXT ---
    {{ other_context }}

Return format:
- On success:

    <headline>
    <technical summary>

- On failure:
    Return a clear error message for network errors, missing config, or invalid responses.

After implementation, make sure to run and fix:

- `ruff format .`
- `ruff check .`
- `mypy .`

For development, document how to run the backend in `README.md`.

2) Tests

Use `pytest`.

Add exactly one happy-path test in `tests/test_commit_summary.py`.

Test requirements:
- Do not mock Ollama calls.
- Provide a small sample `git_diff_output`.
- Call `summarize_git_diff`.
- Use LLM-as-a-judge with a second real Ollama call.
- Judge whether the result:
  - is relevant to the diff,
  - includes a headline,
  - attempts humor,
  - includes a concise technical summary.


For development, document how to run the tests in `README.md`.

No failure tests.
No mocking.

3) requirements.txt

Include only required dependencies, for example:
- mcp
- httpx
- python-dotenv
- jinja2
- pytest

Verification:
- Run the test if configuration is available.
- If the real Ollama endpoint is not configured, explain exactly what is missing and how to run the test later.
```

## Follow-up prompt

Po tom, čo agent nakódil MCP server, nasleduje krátka follow-up, aby sme si otestovali výstup priamo na našom repozitáre.

```text
Use the MCP server you just built. As the git diff input, use the repository you just built, and show me verbatim what the MCP server outputs.
```

## Skutočný výstup lokálneho modelu

V videu vidíme, čo zvládne lokálny model Qwen 3.8 27B na dvoch GPU. Celé demo beží lokálne, bez akéhokoľvek externého cloudového API. Je to komplexný, viac-krokový development od nuly. Rovnako prebeží aj pri väčších existujúcich projektoch, napríklad s miliónom riadkov kódu. Agentovi to dlhšie trvá a spáli viac tokenov na získanie informácií, ktoré potrebuje, ale zvyšok prebieha podobne.
