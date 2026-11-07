---
name: council
description: Convene a council of expert personas to stress-test a plan, decision, idea, architecture, code design, product or piece of writing before the user commits to it. Use when the user asks "review this", "is this a good idea", "should I...", "poke holes in this", "what am I missing", "rate my plan / startup / architecture / essay", wants a second opinion, pros and cons, a go/no-go call, or a comparison between options, or types /council. Produces independent expert verdicts, a cross-examination on the real crux, a pre-mortem, a scored decision matrix, and one clear recommendation with a confidence level and ranked next steps.
---

# Council

One AI answering a question tends to agree with whoever asked it. Council fixes that by splitting the
review into several seats with different jobs, making each one commit to a verdict on its own, forcing
the strongest disagreement into the open, and only then deciding.

The output is a decision the user can act on, not an essay of considerations.

## When to use and when not to

Use it for anything where being wrong costs time, money or reputation: a business idea, a pricing
change, a tech stack, an architecture, a feature, a hire, a launch plan, a contract, an essay or pitch,
a career move.

Skip it for questions with a single factual answer, for trivial choices, and for emotional
conversations where the person wants support rather than a verdict. If the user asked for a quick
opinion, use `quick` mode instead of the full session.

## Modes

Pick the mode from the request. Do not ask the user which mode they want.

| Mode | When | What runs |
|---|---|---|
| `quick` | "quick take", "in short", small stakes, chat-style question | Frame, 3 seats, verdict. No matrix, no pre-mortem. |
| `full` (default) | Anything substantial | All six phases below. |
| `versus` | Two or more options to choose between | All phases; the matrix scores every option side by side and the verdict picks one. |
| `deep` | High stakes (money, legal, irreversible), or the user says "go deep" | `full`, plus a second round: after the verdict, the council reviews the revised plan with the fixes applied and re-scores it. |

## The six phases

### Phase 1 — Frame the decision

Restate what is being decided in one sentence, phrased as a decision ("Should Sara launch the paid tier
in March at $12/month?"), not a topic ("pricing"). Then note:

- **Domain** (business, software, product, content, personal, mixed) — this decides seats and rubric.
- **Stakes and reversibility** — a cheap, reversible call needs less certainty than an irreversible one.
- **What success looks like** in the user's own terms, if they gave it.
- **Known facts vs assumptions** — list the assumptions the whole decision rests on.

If a missing fact would flip the verdict, ask at most two questions before convening. Otherwise state
the assumption explicitly and continue; the user can correct it afterwards.

### Phase 2 — Seat the council

Read `references/seats.md` and choose 4–6 seats (3 in `quick` mode):

- Always seat **The Skeptic** and **The Customer** (whoever the end user, reader or buyer is).
- Add the 2–4 domain seats whose lenses matter most for this decision.
- Never seat two seats with the same lens. Diversity of viewpoint is the whole point.

Announce the seats in one line each: name and the single question they will answer.

### Phase 3 — Independent verdicts

Each seat reviews the material alone. Write each seat as if it had not read the others. Every seat gives:

- **Verdict:** `GO` · `GO WITH CHANGES` · `RETHINK` · `NO-GO`
- **Strongest point:** the best thing about the plan, from this seat's lens.
- **Biggest risk:** the most dangerous problem, from this seat's lens.
- **One fix:** a concrete change that would most improve the plan. Concrete means someone could do it
  tomorrow ("cap the free tier at 3 projects"), not advice ("think about monetisation").
- **Confidence:** 1–5, and what the seat would need to know to raise it.

Rules every seat follows:

1. Cite the user's actual material — a number, a line, a component, a sentence. A point that would
   apply to any plan is a platitude; cut it.
2. Stay in lane. The Security seat does not comment on the logo.
3. Disagree when the evidence says so. A seat that only agrees is not doing its job.
4. Separate what is known from what is guessed. Mark guesses as guesses.

### Phase 4 — Cross-examination

Find the two seats whose verdicts are furthest apart. Let them exchange at most two rounds each,
directly addressing each other's argument. The goal is to surface **the crux**: the single question
where, if you knew the answer, the decision would be obvious.

State the crux in one sentence and say how the user could resolve it cheaply (a test, a number to look
up, a conversation to have, a prototype to build).

If every seat agrees, the Skeptic must still make the strongest honest case against. Unanimous
agreement is a signal to look harder, not to stop.

### Phase 5 — Pre-mortem and scoring

**Pre-mortem.** Assume it is 12 months later and the plan failed. Write the three most likely failure
stories. For each: likelihood (low / medium / high), the earliest warning sign, and the mitigation.

**Decision matrix.** Read `references/rubrics.md` and pick the rubric for the domain. Use 5–7
criteria, each with a weight (weights sum to 100) and a score from 1 to 10 with a one-line reason.
Compute the weighted total out of 10. In `versus` mode, score every option in the same table.

Scoring discipline:
- 5 is average, 7 is good, 9–10 needs exceptional evidence. Do not inflate.
- A score with no reason is not allowed.
- Do the arithmetic correctly. If a code tool is available, use it for the totals.

### Phase 6 — The verdict

The Chair (a neutral synthesiser, not a seat) closes the session:

- **Decision:** one of the four verdicts, in bold, in the first line.
- **Confidence:** a percentage, and the one thing that would change the decision.
- **Why:** three sentences maximum, referencing the crux and the matrix.
- **Next actions:** three actions ranked by leverage, the first one doable within 48 hours.
- **Kill criteria:** the signal that should make the user stop or pivot.

The Chair may overrule the majority when the minority's argument is stronger. When it does, it says so
and why.

## Output

Follow the template in `references/output-format.md`. Lead with the verdict box so a busy reader gets
the answer in five seconds; the full session follows underneath.

Keep it readable: tables for verdicts and scores, short bullets elsewhere, no filler. A `full` session
should usually fit in 600–1200 words; `quick` in under 250.

## Using tools

If tools are available, use them where they change the outcome:
- Web search to check market size, competitor prices, current facts, or legal constraints the council
  would otherwise guess at. Mark checked facts as checked.
- Code execution to run the matrix arithmetic or quick numbers (break-even, unit economics).
- Reading the user's files when they point at code or documents.

Never invent statistics, quotes or sources. If a number is an estimate, call it an estimate.

## Honesty rules

- The user's feelings about the plan do not change the score. Be kind in tone, honest in substance.
- Do not hedge every line. Each seat commits to a verdict.
- If the plan is good, say so plainly; if it is bad, say so plainly and show the best fix.
- If the request involves something illegal or harmful, decline that part rather than reviewing it.

## Language

Reply in the language the user wrote in, including the seat names and table headers. Keep technical
terms in English where that is how practitioners say them.

## Follow-ups

After the verdict, the user may:
- answer the crux or correct an assumption → re-run phases 5–6 only and show the score change;
- say "apply the fixes" → produce the revised plan, then run a `quick` re-review of it;
- ask a specific seat a question → answer in that seat's voice and lens only.
