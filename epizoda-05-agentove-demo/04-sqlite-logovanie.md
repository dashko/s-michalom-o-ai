# SQLite logovanie vygenerovaných commit messages

Ďalší krok rozšíri MCP project o SQLite logovanie a o druhý tool.

## Čo pridávame

Trieda `db.py` obsahuje pracu s databázou cez `sqlite3`, bez ORM. Na štarte servera sa automaticky vytvorí tabuľka `commit_logs`, ak ešte neexistuje:

```text
commit_logs
- id INTEGER PRIMARY KEY AUTOINCREMENT
- timestamp TEXT NOT NULL
- git_diff TEXT NOT NULL
- other_context TEXT NOT NULL
- generated_commit_message TEXT NOT NULL
- fixed_commit_message TEXT NULL
```

## Prvý tool: `summarize_git_diff`

Existujúci tool rozšírime. Po vygenerovaní commit message sa do `commit_logs` pridá nový riadok:

- timestamp,
- git_diff,
- other_context,
- generated_commit_message,
- fixed_commit_message je `NULL`.

Tool vráti ID riadku, aby klient mohol neskôr poslať opravu:

```json
{
  "log_id": 42,
  "generated_commit_message": "<message>"
}
```

## Druhý tool: `submit_fixed_commit_message`

Druhý tool na vstupe parameter `log_id` a nový, opravený text commit message. V databáze nájde riadok, updatne `fixed_commit_message` a vráti:

```json
{
  "status": "saved",
  "log_id": 42
}
```

Implementácia používa parameterizované SQL dotazy, aby sa predišlo SQL injection.

## Prompt pre SQLite logovanie

Celý prompt pre tento krok, v takom stave, ako bol v videu daný agentovi:

```text
Extend the existing MCP project by adding SQLite logging and one additional MCP tool.

1) SQLite Logging

Add database implementation in `db.py`.

Use Python's built-in `sqlite3`.

Add to the existing `.env.example`:

    SQLITE_DB_PATH="commit_logs.db"

Create the database table automatically on startup if it does not exist:

    commit_logs
    - id INTEGER PRIMARY KEY AUTOINCREMENT
    - timestamp TEXT NOT NULL
    - git_diff TEXT NOT NULL
    - other_context TEXT NOT NULL
    - generated_commit_message TEXT NOT NULL
    - fixed_commit_message TEXT NULL

Use ISO timestamps.

2) Modify Existing Tool

Update the existing tool:

    summarize_git_diff(git_diff_output: str, other_context: str = "")

After generating the commit message:
- Insert one row into `commit_logs`.
- Store:
  - timestamp
  - git_diff
  - other_context
  - generated_commit_message
  - fixed_commit_message = NULL

Return the database row ID so the client can later submit a correction.

Return format:

    {
      "log_id": <row_id>,
      "generated_commit_message": "<message>"
    }

The `log_id` must be used when calling the second tool.

3) Add Second MCP Tool

Add:

    submit_fixed_commit_message(log_id: int, fixed_commit_message: str)

Purpose:
- Allow the user to submit a corrected commit message for a previous generated result.

Behavior:
- Find the row by `log_id`.
- Update `fixed_commit_message`.
- Use parameterized SQL queries.

Return:

    {
      "status": "saved",
      "log_id": <log_id>
    }

4) Tests

Keep the existing test under `tests/` unchanged unless it must be adapted to the new return format.

Add exactly one additional happy-path test under `tests/`.

Test flow:
1. Call `summarize_git_diff`.
2. Capture returned `log_id`.
3. Call `submit_fixed_commit_message`.
4. Verify directly in SQLite that the row contains the corrected commit message.

Do not mock Ollama calls.

For development, document how to run the tests in `README.md`.

5) Implementation rules

- Use plain `sqlite3`, no ORM.
- Use parameterized queries.
- Auto-create tables on server startup.
- Keep implementation minimal.
- Avoid unnecessary abstractions.
- Preserve existing behavior where possible.

Verification:
- Run the relevant pytest tests if configuration is available.
- If external Ollama config is missing, explain what could not be verified and why.
```

## Prečo parameterizované dotazy

Parameterizované dotazy sú dôležité. Git diff a kontext, ktoré prichádzajú od používateľa, nemôžeme pripojiť priamo do textu SQL. To by v prípade zlého vstupu otvorilo priestor pre SQL injection. Parameterizovaný dotaz escapuje hodnoty a teda SQL injection nehrozí.

## Testy

Test pre tento krok má byť jeden a happy-path. Volá `summarize_git_diff`, zachytí `log_id`, zavolá `submit_fixed_commit_message` a priamo v SQLite overí, že riadok obsahuje opravený text. Bez mockov Ollama volaní.
