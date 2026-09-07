# Promptimize Backend — API / Store (DRAFT)

Base URL: `https://promptimize.therobot.institute`

Both clients (Chrome extension, VS Code extension) treat this as the canonical
prompt store. Local-first: all reads/writes are cached locally and synced when
reachable.

> **Status: draft.** Resource shapes and auth below are the working contract and
> will evolve with implementation.

## Auth

- Token-based (per-client device token), OAuth-style device flow — TBD.

## Resources

### Prompt

| Field | Type | Notes |
|-------|------|-------|
| `id` | uuid | |
| `title` | string | |
| `body` | text | current prompt text |
| `version` | int | monotonic per prompt |
| `starred` | bool | favorites |
| `tags` | string[] | |
| `input_sections` | `InputSection[]` | typed form fields for hydration |
| `evals` | `Eval[]` | attached eval cases/suites |
| `optimized` | `Optimization[]` | optimizer outputs (incl. NPL form) kept beside the original |

### InputSection

`{ name, type, required, default?, help? }` — rendered as a fill-in form by clients;
hydration substitutes values into `{{name}}` placeholders.

### Eval

`{ id, prompt_id, cases: [{ input, expect }], scorer, last_run, score }` — cases may
reference input sections; runs are recorded per prompt version.

### Optimization

`{ id, prompt_id, base_version, target: "npl" | "generic", body, notes }` — optimized
variants are stored beside the source prompt for side-by-side comparison.

### Template (dynamic formulate)

`{ id, title, body_with_slots, description }` — `formulate(template, user_description)`
returns a hydrated, tailored prompt draft.

## Endpoints (sketch)

```
GET/POST        /v1/prompts
GET/PUT/DELETE  /v1/prompts/{id}
POST            /v1/prompts/{id}/star
GET/POST        /v1/prompts/{id}/versions
GET/POST        /v1/prompts/{id}/evals      POST /v1/prompts/{id}/evals/run
GET/POST        /v1/prompts/{id}/optimizations
GET/POST        /v1/templates               POST /v1/formulate
POST            /v1/sync                    (delta push/pull)
```
