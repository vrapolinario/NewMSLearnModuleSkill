# "Introduction to" module pattern

Use this pattern for a **conceptual** module whose audience is **deciding
whether (or when) a product, service, or feature is right for them**. There's
usually **no hands-on exercise**; the outcome is an informed decision, not a
built artifact.

Reference: Microsoft Learn instructional-design guidance for intro modules
(`help/patterns/level4/id-guidance-intromodules`).

## Title

Always: `Introduction to <product / feature / concept>`.

- Example: "Introduction to Azure Cloud Shell".

## Learning objectives (`abstract`)

Frame objectives around **evaluation and understanding**, not hands-on tasks.
Typical phrasing:

```
abstract: |
  In this module, you will:
  - Evaluate whether <product/feature> is appropriate for your scenario.
  - Describe how <product/feature> works and its key capabilities.
  - Identify when to use <product/feature> and when not to.
```

## Unit sequence

Intro modules follow a recognizable decision-oriented arc:

1. **Introduction** (`1-introduction`) — Present a business scenario where
   someone must decide whether to adopt the technology. State that by the end
   the learner can decide if it fits their needs. 2–3 minutes.
2. **"What is <X>?"** (`2-what-is-<topic>`) — Define the product/feature in
   plain language. What problem it solves, where it fits.
3. **Capabilities / "How it works"** (`3-…`) — Key features and how they work
   conceptually. One concept per unit; add more content units as needed.
4. **"When to use <X>" / decision criteria** (`<k>-when-to-use-<topic>`) — The
   heart of an intro module. Give explicit **criteria** the learner weighs to
   decide. Often a "Decide whether…" framing with bullet criteria or a table of
   "Use it when / Consider alternatives when".
5. **Knowledge check** (`<n>-knowledge-check`) — 3–5 questions that test whether
   the learner can apply the decision criteria. See
   [knowledge-check-guidance.md](knowledge-check-guidance.md). YAML only.
6. **Summary** (`<n+1>-summary`) — Resolve the opening scenario's decision,
   recap the criteria, and link to "Learn more" / a follow-on Standard module.

## Writing guidance per unit

- **Introduction**: scenario + a decision the persona faces. Make clear the
  module helps them *choose*, not *build*.
- **"What is" unit**: concept-first, jargon-light. Analogies help. Explain the
  value proposition.
- **Capability units**: describe each capability and the scenario it enables.
  Conceptual diagrams over step-by-step screenshots.
- **"When to use" unit**: the differentiator. Provide concrete criteria,
  trade-offs, and contrasts with alternatives so the learner can self-assess.
- **Summary**: state the decision the persona reaches and why, recap criteria,
  point to next steps.

## Duration

Intro modules are typically short — often 15–30 minutes total. Keep per-unit
durations modest (2–6 minutes each).

## Style reminders

- Emphasize *understanding* and *decision-making* over recall.
- Second person, present tense, active voice.
- Don't overclaim. Ground capability statements in docs or flag with `TODO:`.
