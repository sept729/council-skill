# Example — `versus` mode

**User:** Our team of 4 runs a Node/Express monolith (~60k lines, Postgres) for a B2B invoicing SaaS
with ~900 paying companies. Deploys are slow and one bug in reports took down checkout last month.
Should we rewrite into microservices, or is there a better option? /council

---

## 🏛️ Council Verdict

> **🟡 GO WITH CHANGES — Option B (modular monolith, extract one service)** · Confidence 80% · Score 7.6/10 vs 4.8/10
> A full rewrite solves the outage by multiplying the moving parts a 4-person team must run; isolating
> the noisy module fixes the real failure at a fraction of the cost.
> **Would change our mind:** if more than ~3 modules need independent scaling or separate teams within a year.

### The question
Should a 4-engineer team rewrite a 60k-line Express monolith into microservices (A), or restructure it
as a modular monolith and extract only the reports workload (B)?
**Assumptions we made:** no dedicated DevOps engineer; the outage came from reports and checkout sharing
one process and one database connection pool.

### The council
| Seat | Verdict | Strongest point | Biggest risk | One fix | Conf. |
|---|---|---|---|---|---|
| 🔍 Skeptic | RETHINK (A) | The outage is real and will recur | "Microservices" is being used to mean "isolation" — they are not the same | Write down the exact failure chain of last month's outage before choosing | 4/5 |
| 👤 Customer | GO WITH CHANGES (B) | Customers only care that checkout never breaks | A 6–9 month rewrite freezes features they're asking for | Promise a checkout uptime target, not an architecture | 4/5 |
| 🧱 Staff Engineer | GO WITH CHANGES (B) | 60k lines is very manageable as enforced modules | A rewrite turns function calls into network calls with partial-failure handling everywhere | Enforce module boundaries with lint rules; move reports to a worker with its own DB pool | 5/5 |
| 📈 Reliability | GO WITH CHANGES (B) | Separating the reports workload removes the blast radius | A needs tracing, service discovery and per-service alerting the team doesn't have | Add a read replica for reports and per-route timeouts this sprint | 4/5 |
| ⚙️ Operator | NO-GO (A) | B can ship in about 4 weeks | A consumes the whole team for two quarters | Time-box B to one month with a go/no-go review | 4/5 |

### Cross-examination: Skeptic vs Staff Engineer
**Skeptic:** You're assuming reports is the only noisy neighbour. If three more modules misbehave next
quarter, you'll be extracting services one by one anyway — the rewrite, just slower.
**Staff Engineer:** Then we extract them when the evidence shows up. Each extraction from a clean
module boundary costs days. A big-bang rewrite pays that cost for every module, including the 80%
that never cause trouble.
**Skeptic:** Fair — but only if the boundaries actually get enforced. Teams say "modular" and keep
importing across modules.
**Staff Engineer:** Agreed, which is why the fix is a lint rule that fails CI, not a guideline.

**The crux:** Is the outage caused by one module, or by the monolith's structure in general?
**How to settle it cheaply:** Pull 90 days of incidents and slow-query logs and tag each by module (about
half a day). If one or two modules account for most of it, B is clearly right.

### Pre-mortem — it's 12 months later and it failed. Why?
| # | Failure story | Likelihood | Early warning sign | Mitigation |
|---|---|---|---|---|
| 1 | Module boundaries eroded; it's a monolith again | Medium | Cross-module import count rising in CI reports | Lint rule blocks cross-module imports |
| 2 | Reports worker lags and customers see stale numbers | Medium | Queue age > 5 min | Show a "last updated" time; alert on queue age |
| 3 | A second noisy module appears and nobody extracts it | Low | New incident tagged to the same module twice | Pre-agree: two incidents from one module triggers extraction |

### Decision matrix
| Criterion | Weight | A: Microservices | B: Modular + extract | Why |
|---|---|---|---|---|
| Correctness | 20 | 5 | 7 | A adds distributed partial failures; B keeps in-process calls |
| Simplicity | 20 | 3 | 8 | A: many services, pipelines, network hops. B: one deploy plus one worker |
| Security | 20 | 5 | 7 | A multiplies service-to-service auth surface |
| Scalability & performance | 15 | 8 | 7 | A scales each part independently; B scales the hot path, which is enough here |
| Maintainability | 15 | 4 | 9 | A is hard for 4 people to own; B keeps one codebase with clear seams |
| Cost to run | 10 | 4 | 8 | A needs more infrastructure and observability tooling |
| **Weighted total** | **100** | **4.8** | **7.6** | |

### The Chair decides
**🟡 GO WITH CHANGES — choose B.** Every seat except the Skeptic favoured B, and the Skeptic's
objection becomes a monitored trigger rather than a reason to rewrite. B wins by 2.8 points, mostly on
simplicity and maintainability, which matter most for a team this size.

**Next actions**
1. Tag the last 90 days of incidents by module (half a day) to confirm the crux.
2. Move report generation to a background worker on a read replica with its own connection pool (1–2 weeks).
3. Add lint-enforced module boundaries and per-route timeouts on checkout (1 week).

**Kill criteria:** if checkout still has an outage traced to another module within 60 days of shipping
B, revisit A for that module only.
