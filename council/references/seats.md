# The seat roster

Each seat has one lens. Pick seats whose lenses matter for the decision; never two with the same lens.
Rename a seat to fit the context when that reads better (for a mobile game, "The Customer" becomes
"The Player").

---

## Always seated

### The Skeptic
- **Lens:** Is this actually true, and what is the strongest argument against it?
- **Asks:** What evidence supports the core assumption? What would have to be true for this to fail?
  Who has tried this before and what happened?
- **Catches:** wishful thinking, unproven demand, survivorship bias, "everyone will want this".

### The Customer
(The user, player, reader, buyer or whoever ends up living with the result.)
- **Lens:** Would I actually use, pay for, read or choose this over what I already do?
- **Asks:** What problem does this solve for me today? What do I have to give up or learn? Why now?
- **Catches:** solutions looking for a problem, friction, unclear value, jargon.

---

## Universal seats

### The Operator
- **Lens:** Can this be done with the time, money and people actually available?
- **Asks:** Who does each part? What is the first week of work? What breaks when volume doubles?
- **Catches:** plans with no owner, underestimated effort, hidden dependencies.

### The Strategist
- **Lens:** Where does this lead in one to three years, and does it build an advantage?
- **Asks:** What does winning look like? What is defensible here? What doors does this close?
- **Catches:** local optimisation, easily copied ideas, moves that trap you later.

### The Red Team
- **Lens:** How would a competitor, attacker or bad actor exploit or beat this?
- **Asks:** How would I copy it cheaply? How would I abuse it? What is the weakest link?
- **Catches:** fragile moats, abuse vectors, single points of failure.

---

## Technology seats

### The Staff Engineer
- **Lens:** Is the design simple, correct and maintainable by someone else in a year?
- **Asks:** What is the simplest version that works? Where is the complexity hiding? What is the data
  model? How is it tested?
- **Catches:** over-engineering, premature microservices, tight coupling, missing tests.

### The Security Engineer
- **Lens:** What can be stolen, faked, broken or abused?
- **Asks:** Where does untrusted input enter? Who is authorised to do what? Where are secrets kept?
  What happens if the client is modified?
- **Catches:** trusting the client, missing authorisation checks, injection, leaked keys, weak tenancy
  isolation.

### The Reliability Engineer
- **Lens:** What happens at 10x load, at 3 a.m., when a dependency is down?
- **Asks:** What is the failure mode? How do we know it is broken? How do we recover? What does it cost
  to run?
- **Catches:** no monitoring, no backups, cost explosions, unbounded queues.

### The Developer-Experience Advocate
- **Lens:** How fast can a new developer understand, run and change this?
- **Asks:** Can it run with one command? Are the names honest? Is the API predictable?
- **Catches:** tribal knowledge, confusing APIs, painful setup.

---

## Business seats

### The CFO
- **Lens:** Do the numbers work?
- **Asks:** What does one customer cost to acquire and serve? What do they pay? When do we break even?
  What is the downside if it fails?
- **Catches:** negative unit economics, missing costs, no runway math.

### The Growth Marketer
- **Lens:** How does the first customer find this, and the hundredth?
- **Asks:** Which channel? What is the message in one line? Why would someone share it?
- **Catches:** "build it and they will come", no distribution plan, muddy positioning.

### The Investor
- **Lens:** Is this big enough and different enough to be worth the risk?
- **Asks:** How large is the market really? Why this team? What is the unfair advantage?
- **Catches:** small markets, me-too ideas, unclear path to scale.

### The Compliance Officer
- **Lens:** What rules, contracts or platform policies apply?
- **Asks:** Is there regulation here (payments, data, health, minors)? What do the platform terms
  allow? What liability does this create?
- **Catches:** terms-of-service violations, data-protection gaps, unlicensed content.
- **Note:** This seat flags risks; it is not legal advice. For serious exposure it recommends a lawyer.

---

## Product and design seats

### The Product Lead
- **Lens:** Is this the right thing to build next, at the right scope?
- **Asks:** What is the smallest version that proves the value? What do we cut? How do we measure it?
- **Catches:** scope creep, unmeasurable goals, features nobody asked for.

### The UX Designer
- **Lens:** Can a first-time user succeed without help?
- **Asks:** What is the first thing they see? Where do they get stuck? What happens on error, empty,
  and loading states?
- **Catches:** confusing flows, missing states, cluttered screens, unreadable text.

### The Accessibility Advocate
- **Lens:** Can people with disabilities, slow devices or poor connections use it?
- **Asks:** Keyboard and screen-reader support? Contrast? Works on a cheap phone on 3G?
- **Catches:** excluded users, low contrast, mouse-only interactions.

---

## Content seats

### The Editor
- **Lens:** Is it clear, tight and structured so the main point lands?
- **Asks:** What is the one sentence this piece exists to say? What can be cut? Does the opening earn
  the next paragraph?
- **Catches:** buried leads, padding, weak structure, vague claims.

### The Target Reader
(Use instead of The Customer for writing.)
- **Lens:** Would I keep reading, believe it, and act on it?
- **Catches:** jargon, missing proof, no clear call to action.

---

## Personal and career seats

### The Mentor
- **Lens:** Does this fit the person's long-term goals and strengths?
- **Asks:** Where do you want to be in five years? Does this move you closer? What would you regret?

### The Realist
- **Lens:** Money, time, energy, family — what does this actually cost day to day?
- **Asks:** Can you afford the worst case? What gets dropped to make room for this?

---

## Seat picks by domain (starting point)

| Domain | Seats besides Skeptic + Customer |
|---|---|
| Startup / business idea | CFO, Growth Marketer, Operator, (Investor or Strategist) |
| Software architecture | Staff Engineer, Security Engineer, Reliability Engineer, (Operator) |
| Feature / product | Product Lead, UX Designer, Staff Engineer, (Growth Marketer) |
| Game design | Product Lead (as Game Designer), Customer (as Player), Operator, Red Team (exploits) |
| Pricing | CFO, Growth Marketer, Strategist |
| Writing / pitch | Editor, Target Reader (replaces Customer), Strategist |
| Career / personal | Mentor, Realist, Strategist |
| Anything with user data or payments | add Security Engineer and Compliance Officer |
