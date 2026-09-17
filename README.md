### Sri Hari Manikandan

Software engineer and security engineer. Eight years building backend systems
and SaaS products; five in application security. Based in India, working with
clients in Europe.

I build the parts of a system that are expensive to get wrong: tenant
isolation, authentication, money arithmetic, compliance with a published
standard. The repositories below are working software with tests, CI and
decision records — not tutorials.

---

#### Selected work

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

TypeScript (strict), Node, Next.js, PostgreSQL, Prisma, Redis, Docker,
GitHub Actions. Python for security tooling. Comfortable in Linux, TLS,
HTTP, and the OWASP corpus.

#### Contact

hacktivatecybersolutions@gmail.com
