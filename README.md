# Promptimize

> Capture, organize, evaluate, and optimize your prompts — with a Chrome extension, a VS Code extension, and a shared prompt store.

**Status:** scaffold / early development · **License:** MIT

## What it does

- **Track** — a personal, synced prompt library; every prompt keeps its edit history.
- **Paste to capture** — clip any prompt you run into straight into your library.
- **Edit** — full editor with versions and diffs between revisions.
- **Star** — pin your go-to prompts to the top.
- **Optimize** — guided prompt improvement, including **Noizu Prompt Lingua (NPL)**
  style conventions — structured, compact, spec-driven prompt syntax with explicit
  assumption tables, friction modules, and response contracts.
- **Evals** — attach eval cases/suites to a prompt, run them, and track scores as the
  prompt evolves.
- **Stub prompts & input forms** — define a prompt with typed **input sections**
  (`{{topic}}`, `{{audience}}`, …); Promptimize renders a form to fill them in and
  produces the hydrated prompt.
- **Dynamic formulate** — start from a template plus a short natural-language
  description of what you need, and Promptimize populates the template into a
  tailored, ready-to-run prompt.

## Clients

| Client | Path | Status |
|--------|------|--------|
| Chrome extension | `chrome/` | scaffold |
| VS Code extension | `vscode/` | scaffold |

## Backend

Both clients sync against the Promptimize API/store at
**`https://promptimize.therobot.institute`** (prompts, versions, stars, evals,
templates). The draft API contract lives in [`docs/BACKEND.md`](docs/BACKEND.md).

The extensions are useful offline-first: the library is cached locally and syncs
when the backend is reachable.

## Noizu Prompt Lingua (NPL)

Prompt optimization supports NPL conventions as a first-class target: prompts can be
stressed, compressed, and restructured into NPL form (assumption tables, intent
reading, friction modules, explicit response protocols) with the optimized output
stored alongside the original for comparison.

## Repository layout (planned)

```
chrome/        # Manifest V3 extension (popup + side panel library, page capture)
vscode/        # VS Code extension (prompt library, editor, eval runner)
docs/          # API contract, NPL optimization notes
```

## License

[MIT](LICENSE)
