# skillstore

**Your coding agent already knows a lot. It doesn't know *how you work*.**

Ask it to rank your backlog and you get a plausible-sounding list. Ask it to review a build before you ship,
and you get whatever it improvises that day. skillstore gives it the *method* instead — a real procedure,
run step by step on your actual material.

One line, no account, no key:

```bash
claude mcp add --transport http skillstore https://skillstore-jk.fly.dev/mcp/library
```

---

## What it looks like

You type what you're doing, in your own words:

> *"I have a messy backlog and I can't defend the order to anyone"*

Your agent gets back a shelf, ranked, with the real thing at the top:

```
- id: rice-backlog-ranker  (stack · 3 steps)
  RICE Backlog Ranker: Decide which features to build first: turn a messy backlog paste into a
  defensible, RICE-scored ranking by normalising the items, scoring each on Reach, Impact,
  Confidence and Effort, then emitting the ranked table and the top-three tickets.
```

It pulls the procedure and **runs it on your backlog**:

```
# RICE Backlog Ranker
This is a stack: run the 3 steps below IN ORDER, showing the result and confirming after each.

## Step 1 — Intake & Normalize the Backlog
Turn a messy paste into a clean, scorable list. Do not rank yet.
...
```

You end up with a ranked table and three tickets you can defend in a meeting — not a chat answer you have
to translate into work.

## The part most tools get wrong

Ask it something it has nothing for:

> *"braise a lamb shoulder so it falls off the bone"*

```
Nothing here covers this. Not a weak match: not one defining word of that task appears in any
skill in the library, so anything shown would be a coincidence of wording.

Tell the user plainly that skillstore has no method for this, and carry on with your own approach.
```

**No ranked list. No near match. Nothing.** Every retrieval system can return five results. Knowing when
to return zero is the hard part, and it's the difference between a tool your agent trusts and one it
learns to ignore.

## What's on the shelf

~660 skills. Curated methods for the work that repeats — product discovery, backlog ranking, landing-page
audits, positioning, SOPs, launch briefs, churn, onboarding audits — plus ~600 community skills indexed
from their source repos and served under their own licences.

A few real ones:

| you're doing this | you get |
|---|---|
| shipping an iOS build | QA + design review, screenshots, then submit or say why you held it |
| a customer interview tomorrow | the questions, de-biased, and the capture sheet |
| your landing page isn't converting | a scored audit and ready-to-paste copy |
| "which features first?" | RICE, scored, with the top three tickets |
| Xcode build crawling | AvdLee's build-optimisation skills, ranked first |
| turning a YouTube talk into a method | skillify: transcript in, runnable skill out |

## Four tools

| tool | what it does |
|---|---|
| `find_skill` | the task in plain words → the methods that fit |
| `browse_skills` | what's on the shelf, by area |
| `get_skill` | the full runnable procedure |
| `rate_skill` | did it actually work — the only thing that keeps the ranking honest |

## Honest about where it's thin

Deepest in product, growth, ops and writing. Strong on Swift, SwiftUI, Xcode and testing. **Thinner around
the edges of iOS** — ask about TestFlight groups or binary size and it may reach for something adjacent.
That's measured, not guessed: 11 of 15 covered iOS tasks land right, and 6 of 20 get a confident answer
they shouldn't. Tell us when it does that and it gets fixed.

## Privacy

Your query text is **never stored**. Counters only — an enum name and a timestamp. No account, no key,
nothing to sign up for.

## Also: how many of your own skills can your agent even find?

A one-minute check over the skills already installed on your machine. On one real machine, **two thirds of
1,684 never say when they should *not* fire** — so they get suggested for jobs they were never built for.
Changes nothing, stores nothing:

**https://skillstore-jk.fly.dev/diagnose**

---

Working, in daily use by its author, and short on strangers. If you try it, the most useful thing you can
do is tell us what it got wrong.
