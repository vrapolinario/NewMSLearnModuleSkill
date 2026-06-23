# New Microsoft Learn Module Skill

A [GitHub Copilot Skill](https://code.visualstudio.com/docs/copilot/copilot-customization)
that helps Microsoft Cloud Advocates and Microsoft Learn authors **start drafting
new Microsoft Learn training modules** — from a topic idea to a review-ready
draft with the correct folder structure, valid YAML, drafted Markdown, required
metadata, and a knowledge-check quiz.

The skill targets the [`MicrosoftDocs/learn-pr`](https://github.com/MicrosoftDocs/learn-pr)
publishing repository conventions and supports two module types:

- **Standard modules** — task/skill based, often with a hands-on exercise.
- **"Introduction to" modules** — conceptual, helping the audience decide
  whether/when to use a product or feature.

> The skill produces a **draft for human review**. Authors remain responsible
> for technical accuracy, brand/style compliance, and opening the pull request.

## What it does

Given a topic idea, GitHub Copilot will:

1. **Gather inputs** — module type, target `learn-pr/<product>/` folder, author
   identity (GitHub + Microsoft aliases), audience role/level, and any source
   material.
2. **Research** the topic from author-provided sources and first-party docs.
3. **Scaffold** the full module folder: `index.yml`, numbered unit `.yml`
   files, `includes/*.md` content files, and a `media/` folder.
4. **Draft the content** unit by unit, in Microsoft Learn style.
5. **Add required metadata**, setting the requesting user as the module
   `author` / `ms.author`.
6. **Generate a knowledge check** (3–5 understanding-focused questions, 3
   options each, one correct, with explanations for every option).
7. **Validate and summarize** the draft with a `TODO:` checklist of items to
   verify before publishing.

## Resulting module layout

The skill generates modules in the `learn-pr` layout. Note that the **repo** is
`MicrosoftDocs/learn-pr` and it contains an inner **folder** also named
`learn-pr/`; module paths below are relative to that inner folder (e.g. the live
sample lives at `learn-pr/azure/intro-to-azure-cloud-shell/`):

```text
learn-pr/<product>/<module-folder-name>/
├── index.yml                     # Module definition + metadata + unit list
├── 1-introduction.yml
├── 2-<slug>.yml                  # Content units
├── <n>-knowledge-check.yml       # YAML only — no Markdown file
├── <n+1>-summary.yml
├── includes/                     # One .md per unit EXCEPT the knowledge check
│   ├── 1-introduction.md
│   ├── 2-<slug>.md
│   └── <n+1>-summary.md
└── media/                        # Images, diagrams, video thumbnails
```

## Installing the skill

Skills are folders containing a `SKILL.md` file. Place this folder where your
GitHub Copilot client discovers skills:

- **Per user (all workspaces):** copy the folder into your Copilot skills
  directory, for example `~/.copilot/skills/new-mslearn-module/`.
- **Per workspace/repo:** include the folder in your repository so collaborators
  share it.

After placing it, restart/reload your editor so the skill is discovered. The
skill activates automatically when you ask Copilot to create or draft a
Microsoft Learn module.

## Using the skill

In GitHub Copilot Chat, describe the module you want, for example:

> Create a new "Introduction to" Microsoft Learn module about Azure Cloud Shell.
> It goes under the `azure` folder. My GitHub alias is `myalias` and my Microsoft
> alias is `myalias`.

Copilot will ask any missing questions, then scaffold and draft the module. When
working outside a real `learn-pr` clone, it generates the module under a local
working folder (e.g. `drafts/learn-pr/<product>/...`) so you can copy it into
your `learn-pr` fork and open a pull request.

## Prerequisites & access

- Publishing to Microsoft Learn requires access to the **private**
  `MicrosoftDocs/learn-pr` repository under the MicrosoftDocs organization. The
  skill drafts content locally; you push to your fork and open a PR through your
  authorized account.
- **Recommended:** enable the [Microsoft Learn Docs MCP](https://github.com/MicrosoftDocs/mcp)
  server so Copilot can ground the draft in first-party Microsoft Learn content
  (`microsoft_docs_search` / `microsoft_docs_fetch`). The skill prefers it over
  generic web fetches. It's optional — the skill falls back to `fetch_webpage`.
- The skill does **not** push, commit, or open PRs on your behalf.

## References

- [Create a module (Microsoft Learn Help)](https://learn.microsoft.com/help/learn/create-a-module)
- [Standard modules guidance](https://learn.microsoft.com/help/patterns/level4/id-guidance-standardmodules)
- [Introduction modules guidance](https://learn.microsoft.com/help/patterns/level4/id-guidance-intromodules)
- [Required metadata for training modules](https://learn.microsoft.com/help/learn/required-metadata-training-modules)
- [Create the scaffold manually](https://learn.microsoft.com/help/learn/create-scaffold-manual)

## Disclaimer

This skill accelerates drafting; it does not replace editorial review.
Always verify product behavior, limits, pricing, and links against official
first-party documentation before publishing. Generated content may contain
`TODO:` markers indicating where author input is required.

## Contributions

Contributions are welcome! Open an issue or PR here to improve the skill, add features, or report bugs. Please follow the [Microsoft Learn contribution guidelines](https://learn.microsoft.com/help/learn/contribute) and [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
