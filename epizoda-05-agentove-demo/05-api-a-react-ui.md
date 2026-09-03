# API a React UI

Posledný krok v deme pridá malú webovú vrstvu. Umožní zobraziť a opraviť uložené commit messages.

## Čo pridávame

Backend dostane minimálne FastAPI endpointy nad existujúcim SQLite:

- `GET /api/commit_logs?page=1&page_size=10`: vráti stránkované riadky.
- `POST /api/commit_logs`: vytvorí nový ručný záznam.
- `PUT /api/commit_logs/{id}`: upráví `fixed_commit_message` na existujúcim riadku.

Frontend je minimálna Vite + React aplikácia pod adresárom `frontend/`:

- `frontend/package.json`,
- `frontend/index.html`,
- `frontend/src/main.tsx`,
- `frontend/src/App.tsx`,
- `frontend/src/api.ts`,
- `frontend/src/App.css`.

UI zobrazí stránkovanú tabuľku s poliami `id`, `timestamp`, `git_diff`, `other_context`, `generated_commit_message`, `fixed_commit_message`. Používateľ vie ísť na ďaľšiu stranu, editovať `fixed_commit_message`, pridať nový záznam a uložiť zmeny cez FastAPI endpointy.

## Playwright test

K tomu agent pridá jeden Playwright test v `tests/e2e/`. Scenár:

1. Spustí server.
2. Otvorí React UI.
3. Prejde na tabuľku commit logs.
4. Upraví existujúci `fixed_commit_message`.
5. Uloží zmeny.
6. Overí, že aktualizovaná hodnota je v tabuľke.

Ak je to potrebné, test naplní databázu seed dát, aby bol deterministický.

## Implementačné pravidlá

- Využívaj existujúcu SQLite vrstvu z `db.py`.
- Bez ORM.
- React komponenty majú zostať malé.
- Pagination má fungovať.
- Žiadne nesúvisiace refakory.
- Po implementácii prejsť `npm run format`, `npm run lint`, `npm run typecheck`, `npm run build`.

## Prompt pre API a React UI

Celý prompt pre tento krok, v takom stave, ako bol daný agentovi:

```text
Extend the existing MCP project by adding a small web interface for viewing and editing commit logs.

1) Backend API

Add minimal FastAPI endpoints to the existing Python server in `server.py`.

Endpoints:

    GET /api/commit_logs?page=1&page_size=10

Returns paginated rows from `commit_logs`.

    POST /api/commit_logs

Creates a new manual entry.

    PUT /api/commit_logs/{id}

Updates `fixed_commit_message` for an existing row.

Requirements:
- Use the existing SQLite database.
- Reuse SQLite access from `db.py`.
- Use parameterized SQL queries.
- Do not introduce an ORM.
- Keep endpoint responses simple JSON.

2) React Interface

Add a minimal Vite + React frontend under `frontend/`.

Structure:
- `frontend/package.json` for frontend scripts and dependencies
- `frontend/index.html` for the Vite entry page
- `frontend/src/main.tsx` for mounting React
- `frontend/src/App.tsx` for the main commit log UI
- `frontend/src/api.ts` for calls to the FastAPI endpoints
- `frontend/src/App.css` for simple styling

Requirements:
- Display a paginated table with:
  - id
  - timestamp
  - git_diff
  - other_context
  - generated_commit_message
  - fixed_commit_message

Features:
- Pagination
- Edit `fixed_commit_message`
- Add a new manual entry
- Save changes through the FastAPI endpoints

Keep styling simple but readable.
No heavy UI framework is required.

After implementation, make sure to run and fix:

- `npm run format`
- `npm run lint`
- `npm run typecheck`
- `npm run build`

3) Serving UI

Add static file handling so the Python server can serve the built UI.

For development, document how to run the frontent in `README.md`.
If you start the React dev server from Python, keep it simple and explain the trade-off.

4) Playwright Test

Add exactly one Playwright test under `tests/e2e/`.

Test scenario:
1. Start the server.
2. Open the React interface.
3. Navigate to the commit log table.
4. Edit an existing `fixed_commit_message`.
5. Save it.
6. Verify the updated value appears in the table.

Keep the test deterministic.
Seed the database if needed.

For development, document how to run the tests in `README.md`.

5) Implementation rules

- Reuse existing SQLite code where possible.
- Do not introduce an ORM.
- Keep React components small.
- Ensure pagination works.
- Keep code clean and focused.
- Do not make unrelated refactors.

Verification:
- Run backend tests.
- Run the Playwright test if dependencies and browsers are installed.
- If something cannot be run, explain the exact missing dependency or command.
```

## Prečo takto

Prompt má jasný rozsah (API + UI + E2E), explicitné pravidlá (bez ORM, reúžia `db.py`) a konkretné verification. Agent vie z tohto promptu priamo extrahovať, čo má spraviť, čo nesmie spraviť a ako overiť výsledok.
