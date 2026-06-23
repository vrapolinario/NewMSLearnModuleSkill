# Standard module pattern

Use this pattern when the learner will **accomplish a task or build a skill** —
something they can *do* afterward. Standard modules are outcome-driven and often
include a hands-on exercise.

Reference: Microsoft Learn instructional-design guidance for standard modules
(`help/patterns/level4/id-guidance-standardmodules`).

## Title

Imperative and task-oriented. Start with a verb describing the outcome.

- Good: "Configure storage accounts", "Build a serverless API with Azure Functions"
- Avoid: noun-only or "Introduction to…" (that's the intro pattern).

## Learning objectives (`abstract`)

3–5 measurable objectives the learner can *do* after the module. Use action
verbs (configure, create, deploy, analyze, secure). Format:

```
abstract: |
  In this module, you will:
  - Create a <thing>.
  - Configure <thing> for <goal>.
  - Verify <outcome>.
```

## Unit sequence

A typical standard module:

1. **Introduction** (`1-introduction`) — Set the scene with a concrete business
   scenario/persona. State what the learner will build/do and the objectives.
   2–3 minutes.
2. **Learning-content units** (`2-…`, `3-…`, …) — One concept or capability per
   unit. Explain *what*, *why*, and *how it works* before any hands-on step.
   Keep each unit focused. Use diagrams and examples.
3. **Exercise unit(s)** (optional but common, `exercise-<slug>`) — Hands-on,
   numbered steps the learner follows, ideally tied to the scenario. If the
   module uses a sandbox/host, note the requirement. Exercises usually have a
   higher `durationInMinutes`.
4. **Knowledge check** (`<n>-knowledge-check`) — 3–5 questions. See
   [knowledge-check-guidance.md](knowledge-check-guidance.md). YAML only.
5. **Summary** (`<n+1>-summary`) — Recap the scenario resolution, restate what
   they accomplished against the objectives, and (if exercise used a sandbox)
   note cleanup. Add "Learn more" links to first-party docs.

## Writing guidance per unit

- **Introduction**: open with a relatable scenario ("Suppose you work at…").
  Tell the learner what they'll be able to do. List objectives. Do not teach
  concepts here.
- **Content units**: teach concept-first. Lead with the problem the feature
  solves. Use one H1 (the unit title is supplied by YAML — start body with H2
  or prose), short paragraphs, bullet lists, and a diagram where it clarifies.
- **Exercise units**: give numbered, verifiable steps. Each step is one action.
  Show expected results/output. Flag where a screenshot is needed with `TODO:`.
- **Summary**: 1 short paragraph closing the scenario + a bullet recap +
  "Learn more" links.

## Duration

Standard modules typically total 20–60 minutes. Set realistic per-unit
`durationInMinutes`; exercises carry most of the time.

## Style reminders

- Second person, present tense, active voice.
- Define a term the first time you use it.
- Don't fabricate steps, output, limits, or pricing — verify against docs or
  mark `TODO:` for the author.
