# Knowledge-check guidance

The knowledge check is a required unit. It has **no Markdown file** — everything
lives in its `<n>-knowledge-check.yml` under a `quiz:` block.

## Rules

- **3–5 questions** per knowledge check.
- Each question **evaluates the learner's understanding** of the module's
  objectives — the ability to apply or reason about concepts — **not** recall of
  trivia, exact UI labels, version numbers, or memorized syntax.
- Each question has **exactly 3 options**.
- **Exactly 1 option is correct** (`isCorrect: true`); the other two are
  `isCorrect: false`.
- **Every option has an `explanation`** stating *why* it is correct or
  incorrect. Explanations teach — they reinforce the concept, they don't just
  say "Correct"/"Wrong".
- Distractors must be plausible (common misconceptions), not obviously absurd.
- Don't include "All of the above" / "None of the above".
- Keep questions independent — one question must not reveal another's answer.

## Question quality checklist

For each question ask: *Does answering this correctly prove the learner met a
learning objective?* If it only proves they memorized a detail, rewrite it to
test application or judgment.

Good (tests understanding):
> Your team needs an ad-hoc shell in the Azure portal without installing
> anything locally. Which capability of Azure Cloud Shell makes this possible?

Weak (tests recall):
> What year was Azure Cloud Shell released?

## YAML shape

```yaml
quiz:
  title: Check your knowledge
  questions:
    - content: "Question stem written as a scenario or concept check?"
      choices:
        - content: "Plausible but incorrect option."
          isCorrect: false
          explanation: "Explain the misconception and why it's wrong."
        - content: "The correct option."
          isCorrect: true
          explanation: "Explain why this is right and reinforce the concept."
        - content: "Another plausible distractor."
          isCorrect: false
          explanation: "Explain why this doesn't fit."
```

Notes:

- The order of choices can vary; the correct answer need not be first.
- Use clear, complete sentences. End option text without trailing punctuation
  inconsistency (be consistent within the quiz).
- Tie each question back to one of the module's `abstract` objectives.
