### Sri Hari Manikandan

Software engineer and security engineer. Eight years building backend systems
and SaaS products; five in application security. Based in India, working with
clients in Europe.

I build the parts of a system that are expensive to get wrong: tenant
isolation, authentication, money arithmetic, compliance with a published
standard, time-zone arithmetic, rate limiting under concurrency. The
repositories below are working software with tests, CI and decision
records — not tutorials — and four of them run together as one deployed
stack.

---

#### Selected work

**[grainops](https://github.com/sriharifortitude/grainops)** — the four repositories below it, deployed as one stack.
`docker compose up` builds eventgrain, grainview, gatelimit and
tablewarden from pinned tags with Postgres, Redis, Prometheus and a
provisioned Grafana dashboard; secrets in `.env` only, one public port,
migrations as a job the API depends on, backups, a runbook. A smoke test
in CI ingests through the public port, waits for rollups, proves the
rate limit under a 400-request burst, and runs the data-quality gate.

**[gatelimit](https://github.com/sriharifortitude/gatelimit)** — rate-limiting reverse proxy in Go.
Token bucket and sliding window over an in-process store or Redis, where
Lua scripts make decisions atomic across instances (100 concurrent
requests through two clients: exactly 50 pass, under the race detector).
IETF `RateLimit-*` headers, fail-open with a per-instance fallback or
fail-closed, trusted-proxy handling, Prometheus metrics. Go 1.27, MIT.

**[grainview](https://github.com/sriharifortitude/grainview)** — the dashboard for eventgrain.
Series, funnel and retention views with hand-written SVG charts: each
chart is a named image with a generated one-sentence description and a
data table behind a disclosure; funnels and retention grids are real
tables. Colour never the only channel; axe-clean; saved views; CSV.
React 19, no chart library, BSL 1.1.

**[eventgrain](https://github.com/sriharifortitude/eventgrain)** — self-hosted product analytics on Postgres.
Month-partitioned events with plain SQL migrations; count, unique, funnel
and retention queries bucketed in the project's time zone; daily rollups
the planner uses only when the answer is provably identical to raw, and
every response says which it used; per-person erasure that invalidates
aggregates; retention by partition drop; streamed CSV export. The
integration fixture straddles a clock change. Hono, pg, BullMQ, BSL 1.1.

**[openslot](https://github.com/sriharifortitude/openslot)** — appointment booking for a European practice.
Slot engine computed in wall-clock time so DST transitions give the slots a
receptionist would offer, pinned by tests on both transitions. WAI-ARIA grid
calendar with a keyboard suite and axe-core checks; English, German and
French through `Intl` with a typed message table; double booking prevented
by a partial unique index and proven under concurrent requests. The
accessibility statement lists what has not been verified as carefully as
what has. React 19, Hono, Prisma, BSL 1.1.

**[ubl-billing](https://github.com/sriharifortitude/ubl-billing)** — EN 16931 / Peppol BIS Billing 3.0 e-invoicing engine.
Build, calculate, validate and parse the UBL documents behind the EU's B2B
e-invoicing mandates (XRechnung, Peppol). Exact decimal arithmetic; 78
validation rules cited by their specification identifiers; credit notes;
serialise → parse round-trip proven by test. TypeScript, MIT.

**[hookrelay](https://github.com/sriharifortitude/hookrelay)** — outbound webhook delivery service.
Signed with Standard Webhooks (tested against the spec's vector), fixed and
quotable retry schedule, dead-lettering and replay, idempotent publishing
and idempotent delivery, circuit breaker, OpenAPI 3.1 generated from the
route schemas. Fastify, Prisma, BullMQ, BSL 1.1.

**[bailey](https://github.com/sriharifortitude/bailey)** — multi-tenant SaaS for continuous web security monitoring.
Postgres row-level security as the isolation backstop, mutation-tested;
Argon2id and opaque sessions; RBAC with invariant tests; domain-ownership
verification; BullMQ scan pipeline with regression detection; GDPR export,
erasure and retention. Every form works without JavaScript. Next.js 15,
Prisma, BSL 1.1.

**[tablewarden](https://github.com/sriharifortitude/tablewarden)** — data-quality checks as a CI gate.
Eight kinds of check declared in TOML, each compiled to one SQL statement
against Postgres, SQLite or CSV (loaded into SQLite); failing rows sampled
into terminal, JSON or JUnit reports; read-only sessions; exit codes that
distinguish "found problems" from "could not look". Python 3.12, mypy
strict, zero runtime dependencies, MIT.

**[parapet-scan](https://github.com/sriharifortitude/parapet-scan)** — web security posture audit engine.
Nineteen checks across headers, TLS, cookies, CORS, disclosure and content
integrity. Evidence collected once and shared, so a full scan is ~16
requests regardless of check count. Terminal, JSON, SARIF and HTML output;
CI gate; ships its own deliberately misconfigured lab so the integration
tests run against real HTTP. TypeScript, MIT.

---

#### How I work

- Decisions that weren't obvious get an ADR recording what was rejected and what the choice costs.
- Tests state their expected values from hand-worked arithmetic, not from the code's output.
- Coverage claims are honest. A rule that can't fail isn't counted as implemented.
- Commit history is incremental and explains reasoning; there is no "initial commit" containing the whole project.
- Licensing is deliberate per project: tools are MIT, products are source-available.

#### Stack

TypeScript (strict), Node, React, Next.js, Go, PostgreSQL (partitioning,
window functions, plain SQL as readily as Prisma), Redis, Docker, GitHub
Actions. Accessibility to WCAG 2.2 AA and i18n via `Intl`. Python (3.12, typed, ruff/mypy strict) for data and security tooling. Comfortable in Linux, TLS,
HTTP, and the OWASP corpus.

#### Contact

hacktivatecybersolutions@gmail.com
