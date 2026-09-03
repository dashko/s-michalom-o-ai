# Project instructions

This project is a developer tool for generating commit messages from `git diff`.

## Stack

- Python 3.12
- SQLite directly; no ORM
- React
- Docker

## Implementation rules

- Keep changes small, focused, and easy to review.
- Follow existing file structure, naming, and style.
- Reuse existing patterns before adding new ones.
- Do not add dependencies unless the user approves them.
- Do not hard-code secrets, tokens, or private endpoints.
- Do not modify unrelated files.

## Verification

Before finishing, run the relevant checks.

For Python changes, run the applicable commands:

- `ruff format .`
- `ruff check .`
- `mypy .`
- `python -m compileall .`
- `pytest`

For frontend changes, run the applicable commands if they exist in `package.json`:

- `npm run format`
- `npm run lint`
- `npm run typecheck`
- `npm run build`
- `npm test`

For browser-flow changes, add or run a Playwright test, for example `npm run test:e2e`.

## Safety

- Never commit `.env` files or secrets.
- Ask before deleting files.
- Ask before destructive database changes.
- Ask before deploy, push, or production-like commands.

## Git

- Check `git diff` before finishing.
- The diff is the main review artifact.
- Do not commit unless the user asks.
- Do not push unless the user explicitly asks.

## Ask first

Ask before editing when the task is ambiguous, requires a new dependency, changes a public API, changes the database schema, or needs credentials/external-system access.
