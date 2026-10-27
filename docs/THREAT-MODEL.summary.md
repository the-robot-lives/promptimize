# Threat Model — Summary

Promptimize is **scaffold-stage** — no client or backend code in-repo. This
model covers the *declared* surface from `README.md` / draft `docs/BACKEND.md`;
no mitigation is implemented yet.

**Crown jewels:** the prompt library — prompt bodies, edit history, eval cases,
optimizer outputs (often proprietary IP; prompts frequently contain pasted
sensitive material).

**Trust boundaries:** (1) internet ↔ API `https://promptimize.therobot.institute`
(HTTPS; auth defined as "TBD"); (2) extension ↔ host; (3) client ↔ local cache;
(4) backend ↔ unspecified store.

**Register (all open):**

| ID | Severity | STRIDE | Gap |
|----|----------|--------|-----|
| T-001 | High | Spoofing/Elevation | API auth undefined ("TBD") |
| T-002 | High | Info disclosure | Confidential prompt data; no at-rest encryption / scoping specified |
| T-003 | Medium | Info disclosure | Local-first caches unprotected on client disk |
| T-004 | Medium | Tampering | `/v1/sync` delta has no authenticity model |
| T-005 | Medium | Elevation/Info disclosure | Page capture with no sanitization/origin allow-list |
| T-006 | Low | Repudiation | No who-changed-what audit |
| T-007 | Low | DoS | No rate limiting declared |

**Coverage:** 0 mitigated · 0 partial · 7 open (to-implement checklist).

**Residual risk:** no runnable artifact ships, so no live exposure today;
T-001/T-002 must close before any non-team use. Only verifiable perimeter fact:
the API base URL is HTTPS.

→ Full detail: [THREAT-MODEL.md](THREAT-MODEL.md)
