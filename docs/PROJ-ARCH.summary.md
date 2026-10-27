# Project Architecture — Summary

Promptimize is a **scaffold-stage** prompt library: two clients (Chrome MV3
extension, VS Code extension) over one shared, server-backed prompt store at
`https://promptimize.therobot.institute`. No client or backend source exists in
the repo yet — the design below is the *declared* plan from `README.md` and the
draft `docs/BACKEND.md`.

**Style:** local-first clients over a central sync API (`POST /v1/sync` deltas);
library cached locally, synced opportunistically.

**Components:** Chrome extension (`chrome/`, planned) · VS Code extension
(`vscode/`, planned) · Promptimize API (draft contract) · per-client local cache.

**Data flow:** clients read/write local cache → delta sync → API → store
(prompts, versions, stars, evals, templates, optimizations). Edits produce
monotonic versions; evals and optimizer outputs stored beside the source prompt.

**Stack:** HTTPS REST `/v1` JSON · hosting `promptimize.therobot.institute` ·
MIT. Persistence technology unspecified in-repo.

**Key decisions:** two clients one store; local-first; optimization outputs
persisted for comparison; first-class NPL conventions.

→ Full detail: [PROJ-ARCH.md](PROJ-ARCH.md)
