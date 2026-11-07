<div align="center">

# 🏛️ Council

### Stop asking one AI that agrees with you. Ask a council that argues first.

An Agent Skill that makes your AI convene a panel of expert personas to stress-test any plan,
decision, idea, architecture or draft — then hands you **one verdict, a score, and three next steps**.

[![License: MIT](https://img.shields.io/badge/License-MIT-gold.svg)](LICENSE)
![Works with Claude](https://img.shields.io/badge/Claude-Skill-orange)
![Any LLM](https://img.shields.io/badge/Any_LLM-prompt_compatible-blue)

[English](#why) · [العربية](#بالعربي)

</div>

---

## Why

Ask an AI "is my idea good?" and it will usually find a way to say yes. It reads your excitement and
mirrors it. That's comfortable and useless when real money or months of work are on the line.

**Council** changes how the AI thinks before it answers:

1. **Splits the review into seats** — a Skeptic, your Customer, and 2–4 domain experts (CFO, Staff
   Engineer, Security, UX, Editor… 20 seats to choose from).
2. **Forces independent verdicts** — each seat commits to `GO`, `GO WITH CHANGES`, `RETHINK` or
   `NO-GO`, with one concrete fix, before seeing the others.
3. **Drags the disagreement into the open** — the two most opposed seats cross-examine each other
   until the *crux* appears: the one question that actually decides it.
4. **Runs a pre-mortem** — "it's a year later and it failed — why?"
5. **Scores it** — a weighted decision matrix with domain rubrics and honest scoring rules.
6. **Decides** — a neutral Chair gives one verdict, a confidence %, ranked next actions and kill criteria.

## What it looks like

> **🟡 GO WITH CHANGES — Option B (modular monolith, extract one service)** · Confidence 80% · Score 7.6/10 vs 4.8/10
> A full rewrite solves the outage by multiplying the moving parts a 4-person team must run; isolating
> the noisy module fixes the real failure at a fraction of the cost.
> **Would change our mind:** if more than ~3 modules need independent scaling within a year.

| Seat | Verdict | Biggest risk | One fix |
|---|---|---|---|
| 🔍 Skeptic | RETHINK | "Microservices" is being used to mean "isolation" | Write down the exact failure chain first |
| 🧱 Staff Engineer | GO WITH CHANGES | Function calls become network calls everywhere | Lint-enforced module boundaries |
| 📈 Reliability | GO WITH CHANGES | No tracing or per-service alerting | Read replica + per-route timeouts |

**The crux:** Is the outage caused by one module, or by the monolith's structure in general?

👉 Full session: [`council/examples/versus-microservices.md`](council/examples/versus-microservices.md)

## Modes

Council picks the mode from how you ask. No configuration.

| Mode | Trigger | Runs |
|---|---|---|
| **quick** | "quick take", small decisions | 3 seats + verdict, under 250 words |
| **full** | default | All six phases |
| **versus** | "A or B?", comparing options | Side-by-side matrix, picks a winner |
| **deep** | high stakes, "go deep" | Full session, then re-reviews your plan with the fixes applied |

## Install

### Claude Code
```bash
git clone https://github.com/sept729/council-skill.git
mkdir -p ~/.claude/skills
cp -r council-skill/council ~/.claude/skills/
```
For a single project, copy it to `.claude/skills/council/` inside the repo instead.

### Claude apps (web, desktop, mobile)
Zip the `council` folder and upload it as a custom skill in Claude's settings.

### Any other AI (ChatGPT, Gemini, Cursor, local models)
Paste the contents of `council/SKILL.md`, followed by `references/seats.md`, `references/rubrics.md`
and `references/output-format.md`, into your custom instructions, a custom GPT / Gem, or your editor's
rules file. It is plain Markdown and works with any capable model.

## Use it

Just ask naturally — the skill triggers on review-style requests:

```
Is it a good idea to quit my job and freelance full time? Here's my situation: ...
Review this pricing page copy before I launch tomorrow.
Postgres or MongoDB for a multi-tenant SaaS with heavy reporting? /council
Poke holes in my startup idea: a marketplace for second-hand car parts in Egypt.
Go deep on this contract offer — I have to answer by Friday.
```

Follow-ups work too:
- *"We actually have 2,000 customers, not 900"* → re-scores with the new fact
- *"Apply the fixes"* → rewrites your plan and runs a quick re-review
- *"Ask the CFO: what price would you set?"* → answers in that seat's voice

## How it stays honest

- Every point must cite **your** material — a number, a line, a component. Generic advice is cut.
- Scores have a fixed scale (5 is average, 9–10 needs exceptional evidence) and every score needs a reason.
- If every seat agrees, the Skeptic is required to make the strongest honest case against.
- The Chair can overrule the majority — and must say why.
- With web search or code tools available, it checks facts and does the math instead of guessing.

## Customize

- **Add a seat:** append it to `council/references/seats.md` with a lens, questions and what it catches.
- **Add a rubric:** append a table to `council/references/rubrics.md`.
- **Change the look:** edit `council/references/output-format.md`.

## Structure

```
council/
├── SKILL.md
├── references/
│   ├── seats.md
│   ├── rubrics.md
│   └── output-format.md
└── examples/
    └── versus-microservices.md
```

## Contributing

New seats, rubrics and example sessions are welcome. Open a PR with one change per PR and an example
of the output it produces.

## License

[MIT](LICENSE) © 2026 Tameem Yaser (Zeal) · [SEPT](https://sept.cloud)

---

<div dir="rtl">

## بالعربي

### بطّل تسأل AI واحد بيوافقك على كل حاجة. اسأل مجلس بيتخانق الأول.

**Council** هي Skill بتخلي الـ AI يعمل مجلس خبراء يراجع أي فكرة أو قرار أو كود أو خطة قبل ما تنفذها،
وفي الآخر يديك **قرار واحد واضح + تقييم + ٣ خطوات تعملها**.

**بتشتغل إزاي؟**
١. بتقسم المراجعة على كراسي: المشكك، والعميل، و٢–٤ خبراء حسب الموضوع (مدير مالي، مهندس، أمان، مصمم…).
٢. كل كرسي بيحكم لوحده: `GO` أو `GO WITH CHANGES` أو `RETHINK` أو `NO-GO`، ومعاه تعديل عملي واحد.
٣. أكتر اتنين مختلفين بيتناقشوا لحد ما تبان **النقطة الحاسمة**.
٤. Pre-mortem: "عدّت سنة والمشروع فشل… ليه؟"
٥. مصفوفة تقييم بأوزان ودرجات من ١٠.
٦. رئيس المجلس بيدي القرار النهائي ونسبة الثقة والخطوات الجاية.

**التثبيت:** انسخ فولدر `council` في `~/.claude/skills/` لو بتستخدم Claude Code، أو اضغطه zip وارفعه كـ skill
في Claude، أو الصق محتوى الملفات في التعليمات المخصصة لأي AI تاني.

**الاستخدام:** اسأل عادي بأي لغة، والمجلس هيرد بنفس لغتك:
```
هل فكرة إني أعمل متجر قطع غيار أونلاين في مصر فكرة كويسة؟ /council
```

</div>
