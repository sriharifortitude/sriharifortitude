### Sri Hari Manikandan

Software engineer and security engineer. Eight years building backend
systems and SaaS products; five in application security. Based in India,
working remotely with clients in Europe. Available for contract work:
backend and platform engineering, and application security reviews.

I build the parts of a system that are expensive to get wrong: tenant
isolation, authentication, money and time-zone arithmetic, compliance
with a published standard, rate limiting under concurrency. Everything
below is working software with tests, CI and decision records, and four
of the repositories run together as one deployed stack.

**Start here:** [grainops](https://github.com/sriharifortitude/grainops)
— the analytics stack as `docker compose up` or `helm install`, each
proven end to end in CI.

---

#### An analytics platform, deployed together

| | |
| --- | --- |
| [grainops](https://github.com/sriharifortitude/grainops) | Deployment two ways — Compose for one host, a Helm chart for Kubernetes — from pinned, published images: rootless containers, migrations before readiness, default-deny NetworkPolicy, Prometheus/Grafana, backups, runbook. Both paths proven end to end in CI (the Helm path on kind), which found three configuration bugs before a user could. |
| [eventgrain](https://github.com/sriharifortitude/eventgrain) | Self-hosted product analytics. Month-partitioned events in plain SQL; count, unique, funnel and retention in the project's time zone; rollups used only when provably identical to raw; GDPR erasure; retention by partition drop. TypeScript, BSL 1.1. |
| [grainview](https://github.com/sriharifortitude/grainview) | Its dashboard. Hand-written SVG charts that screen readers can read: a named image with a generated description, and the numbers in a table. React 19, no chart library, BSL 1.1. |
| [gatelimit](https://github.com/sriharifortitude/gatelimit) | Rate-limiting reverse proxy. Token bucket and sliding window, in-process or Redis with Lua scripts; 100 concurrent requests across two instances admit exactly 50, under the race detector. Go, MIT. |
| [tablewarden](https://github.com/sriharifortitude/tablewarden) | Data-quality checks as a CI gate: TOML rules compiled to one SQL statement each, over Postgres, SQLite or CSV; JUnit output; exit codes that separate "found problems" from "could not look". Python 3.12, MIT. |

#### Products

| | |
| --- | --- |
| [openslot](https://github.com/sriharifortitude/openslot) | Appointment booking for a European practice. DST-correct slot engine pinned by tests on both transitions; WAI-ARIA calendar with a keyboard suite; English, German, French via `Intl`; double booking prevented by a unique index and proven under concurrent requests. Its accessibility statement lists what was *not* verified. React 19, Hono, BSL 1.1. |
| [bailey](https://github.com/sriharifortitude/bailey) | Multi-tenant SaaS for continuous web security monitoring. Postgres row-level security as the isolation backstop, mutation-tested; Argon2id and opaque sessions; RBAC with invariant tests; GDPR export, erasure, retention; every form works without JavaScript. Next.js 15, BSL 1.1. |

| [camtmatch](https://github.com/sriharifortitude/camtmatch) | Bank-statement reconciliation for accounts receivable. ISO 20022 camt.053 in (all versions in circulation, DTDs refused); payments matched to open invoices by ISO 11649 reference, invoice numbers in the remittance text, then payer IBAN — and every match explains itself in sentences. Amount alone never matches; a statement that doesn't balance applies nothing. Java 21, Spring Boot 4, Postgres, Testcontainers, BSL 1.1. |
| [dsarclock](https://github.com/sriharifortitude/dsarclock) | GDPR data subject request register. Deadlines counted the way EU law counts a month (Regulation 1182/71: short months, weekends, the controller's national holidays with Easter computed); Art. 12 rules enforced — an extension must come within the first month, a refusal is late after the original month even when extended; an audit trail the database itself refuses to edit. .NET 10, EF Core, Postgres, BSL 1.1. |

#### Libraries and tools

| | |
| --- | --- |
| [ubl-billing](https://github.com/sriharifortitude/ubl-billing) | EN 16931 / Peppol BIS Billing 3.0 e-invoicing engine. Exact decimal arithmetic, 78 validation rules cited by their specification identifiers, credit notes, serialise → parse round-trip proven by test. TypeScript, MIT. |
| [hookrelay](https://github.com/sriharifortitude/hookrelay) | Outbound webhook delivery. Standard Webhooks signing tested against the spec's vector, quotable retry schedule, dead-lettering and replay, idempotent publish and delivery, circuit breaker, OpenAPI from the route schemas. Fastify, BullMQ, BSL 1.1. |
| [parapet-scan](https://github.com/sriharifortitude/parapet-scan) | Web security posture audit: nineteen checks over headers, TLS, cookies, CORS and disclosure from ~16 requests per scan; terminal, JSON, SARIF and HTML output; ships a deliberately misconfigured lab so the integration tests hit real HTTP. TypeScript, MIT. |
| [tfwarden](https://github.com/sriharifortitude/tfwarden) | Terraform plan scanner: ten AWS checks — public buckets, security groups open to the internet, unencrypted storage, wildcard IAM — read from `terraform show -json` rather than re-implemented HCL evaluation. An attribute Terraform can't resolve yet is reported `indeterminate`, never guessed pass or fail. Go, MIT. |

---

#### How I work

- Decisions that weren't obvious get an ADR recording what was rejected and what the choice costs.
- Tests state their expected values from hand-worked arithmetic, not from the code's output.
- READMEs say what was verified and what was not; a rule that can't fail isn't counted as implemented.
- Commit history is incremental and explains reasoning; there is no "initial commit" containing the whole project.
- Licensing is deliberate per project: tools are MIT, products are source-available.

#### Stack

TypeScript (strict), Node, React, Next.js · Java 21, Spring Boot · C#, .NET 10, EF Core · Go · Python 3.12 (typed,
ruff/mypy strict) · PostgreSQL (partitioning, window functions, plain SQL
as readily as an ORM), Redis · Docker, Kubernetes/Helm, GitHub Actions,
Prometheus/Grafana
· WCAG 2.2 AA and `Intl`-based i18n · Linux, TLS, HTTP, the OWASP corpus.

#### Contact

hacktivatecybersolutions@gmail.com
