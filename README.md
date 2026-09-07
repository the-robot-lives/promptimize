# Promptimize

**Repo:** https://github.com/the-robot-lives/promptimize

> Capture, organize, evaluate, and optimize your prompts — with a Chrome extension, a VS Code extension, and a shared prompt store.

**Status:** scaffold / early development · **License:** MIT

## Why

Prompts are the reusable capital of AI work, but they usually live scattered in chat scrollback and editor scratch files with no history, no evaluation, and no structure. Promptimize gives them a versioned, synced home with eval tracking and guided optimization — including first-class support for **Noizu Prompt Lingua (NPL)** conventions.

## What

Two clients over one shared store:

| Client | Path | Status |
|--------|------|--------|
| Chrome extension | `chrome/` | scaffold |
| VS Code extension | `vscode/` | scaffold |

- **Track** — a personal, synced prompt library; every prompt keeps its edit history
- **Paste to capture** — clip any prompt you run into straight into your library
- **Edit** — full editor with versions and diffs between revisions
- **Star** — pin your go-to prompts to the top
- **Evals** — attach eval cases/suites to a prompt, run them, and track scores as the prompt evolves
- **Stub prompts & input forms** — define a prompt with typed input sections (`{{topic}}`, `{{audience}}`, …); Promptimize renders a form and produces the hydrated prompt
- **Dynamic formulate** — start from a template plus a short natural-language description, and Promptimize populates the template into a ready-to-run prompt
- **Optimize** — guided prompt improvement, including NPL-style optimization: prompts can be stressed, compressed, and restructured into NPL form (assumption tables, intent reading, friction modules, explicit response protocols), with the optimized output stored alongside the original for comparison

## Backend

Both clients sync against the Promptimize API/store at **`https://promptimize.therobot.institute`** (prompts, versions, stars, evals, templates). The draft API contract lives in [`docs/BACKEND.md`](docs/BACKEND.md). The extensions are useful offline-first: the library is cached locally and syncs when the backend is reachable.

## Repo Layout (planned)

```
chrome/        # Manifest V3 extension (popup + side panel library, page capture)
vscode/        # VS Code extension (prompt library, editor, eval runner)
docs/          # API contract, NPL optimization notes
```
