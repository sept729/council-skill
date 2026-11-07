# Output template

Use this structure. Translate every heading and label into the user's language. Drop sections that the
mode does not run (`quick` skips the matrix and pre-mortem).

---

```
## 🏛️ Council Verdict

> **<VERDICT>** · Confidence <NN>% · Score <X.X>/10
> <One sentence: the decision and the main reason.>
> **Would change our mind:** <the single fact that would flip it>

### The question
<One-sentence decision statement.>
**Assumptions we made:** <only the ones that matter; the user can correct them>

### The council
| Seat | Verdict | Strongest point | Biggest risk | One fix | Conf. |
|---|---|---|---|---|---|
| 🔍 Skeptic | RETHINK | … | … | … | 3/5 |
| 👤 Customer | GO WITH CHANGES | … | … | … | 4/5 |
| … | | | | | |

### Cross-examination: <Seat A> vs <Seat B>
**<Seat A>:** <argument>
**<Seat B>:** <rebuttal>
**<Seat A>:** <response>
**<Seat B>:** <response>

**The crux:** <the one question that decides it>
**How to settle it cheaply:** <test / lookup / conversation, with a time estimate>

### Pre-mortem — it's 12 months later and it failed. Why?
| # | Failure story | Likelihood | Early warning sign | Mitigation |
|---|---|---|---|---|
| 1 | … | High | … | … |
| 2 | … | Medium | … | … |
| 3 | … | Low | … | … |

### Decision matrix
| Criterion | Weight | Score | Why |
|---|---|---|---|
| … | 20 | 7 | … |
| **Weighted total** | **100** | **X.X** | |

(In `versus` mode add one Score column per option and a total row for each.)

### The Chair decides
**<VERDICT>.** <Up to three sentences, referencing the crux and the matrix. If overruling the
majority, say so and why.>

**Next actions**
1. <Highest leverage, doable within 48 hours>
2. <…>
3. <…>

**Kill criteria:** <the signal to stop or pivot, with a number or date where possible>
```

---

## Verdict labels

| Label | Meaning |
|---|---|
| ✅ GO | Do it as planned. |
| 🟡 GO WITH CHANGES | Do it after the listed fixes. |
| 🟠 RETHINK | The goal is fine; the approach needs rework. |
| ⛔ NO-GO | Don't do it; here is what to do instead. |

## Seat icons (optional, keep consistent)

🔍 Skeptic · 👤 Customer · ⚙️ Operator · ♟️ Strategist · 🎯 Red Team · 🧱 Staff Engineer ·
🔐 Security · 📈 Reliability · 🛠️ DX · 💰 CFO · 📣 Growth · 💼 Investor · ⚖️ Compliance ·
🧭 Product · 🎨 UX · ♿ Accessibility · ✍️ Editor · 📖 Reader · 🧑‍🏫 Mentor · 🧮 Realist

## Quick mode template

```
## 🏛️ Council — quick take
> **<VERDICT>** · Confidence <NN>%

| Seat | Verdict | Key point |
|---|---|---|
| 🔍 Skeptic | … | … |
| 👤 Customer | … | … |
| <domain seat> | … | … |

**Crux:** <one line>
**Do this next:** <one action>
```
