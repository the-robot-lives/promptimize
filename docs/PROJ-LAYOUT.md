# Project Layout

<!-- 〚📁:fed9ec92-3e48-5d4c-a6c9-f011504593ab〛 PROJ-LAYOUT :: Navigable map of the promptimize repository structure. -->

Promptimize is a **scaffold-stage** repository. It currently contains no
application source: the planned `chrome/` and `vscode/` client directories and
any backend service code do not exist yet. What is present is the project
entry point, a draft backend API contract, and this documentation set.

```
promptimize/
├── .meta/
│   └── pointers.yaml           # doc-pointer store — 2 file anchors (README, docs/BACKEND.md)
├── docs/
│   ├── BACKEND.md              # Draft API / store contract (resources, endpoints, auth)
│   ├── PROJ-LAYOUT.md          # This file — repository map
│   ├── PROJ-LAYOUT.summary.md  # Tree-only quick reference
│   ├── PROJ-ARCH.md            # Architecture overview
│   ├── PROJ-ARCH.summary.md    # Architecture summary
│   ├── PROJ-SCHEMA.md          # Data-model reference (draft API shapes)
│   ├── PROJ-SCHEMA.summary.md  # Data-model summary
│   ├── THREAT-MODEL.md         # Threat model
│   └── THREAT-MODEL.summary.md # Threat-model summary
├── .gitignore                  # Node/build, VS Code test, env, OS/editor ignores
├── LICENSE                     # MIT (the-robot-lives)
└── README.md                   # Entry point — what/why, clients, backend pointer
```

## Directory Notes

| Path | Contents |
|------|----------|
| `.meta/pointers.yaml` | Generated doc-pointer store. Do not hand-edit; reconcile with `doc-pointers build --write`. |
| `docs/BACKEND.md` | The only substantive design artifact: draft resources (`Prompt`, `InputSection`, `Eval`, `Optimization`, `Template`) and endpoint sketch for the shared store at `https://promptimize.therobot.institute`. |
| `README.md` | Project entry point: Why, What (feature list), Backend pointer, planned repo layout. |

## Planned-but-absent Directories

The README lists these as *planned*; none exists in the checkout:

```
chrome/    # Manifest V3 extension (popup + side panel library, page capture)
vscode/    # VS Code extension (prompt library, editor, eval runner)
```

## Files Requiring Setup

None. There is no build system, no dependency manifest, no environment template,
and no `.envrc`. The repo is documentation-only at this commit.

## Maintenance

- Regenerate the tree when `chrome/`, `vscode/`, or backend code lands; this map
  should then grow real source sections.
- Keep `PROJ-LAYOUT.summary.md` tree aligned with the block above.
