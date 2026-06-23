# Module folder structure & naming conventions

This is the canonical layout for a module in the `MicrosoftDocs/learn-pr`
repository. A module is a folder of related **units** plus its YAML index and
media.

## Repo vs. folder (important)

The **repository** is `MicrosoftDocs/learn-pr`. Inside it there is a top-level
**folder that is also named `learn-pr/`**. All module content lives under that
inner folder. So the path **inside the repo** is:

```
learn-pr/<product>/<module-folder-name>/        # path within the repo
```

For example, the live sample module is at
`https://github.com/MicrosoftDocs/learn-pr/tree/main/learn-pr/azure/intro-to-azure-cloud-shell`
— that is repo `learn-pr` → folder `learn-pr` → `azure` → `intro-to-azure-cloud-shell`.
Throughout this skill, paths that start with `learn-pr/` mean that inner folder.

## Where the module lives

```
learn-pr/<product>/<module-folder-name>/
```

- `<product>` is the top-level subject folder. Azure content goes in `azure`.
  Other examples: `azure-data`, `m365`, `dynamics365`, `github`, `dotnet`,
  `ai`, `security`, `power-platform`, `data-ai`. Confirm with the author which
  folder their team publishes to.
- `<module-folder-name>` is kebab-case and descriptive. For **Introduction to**
  modules prefer `intro-to-<topic>` (for example `intro-to-azure-cloud-shell`).
  For **Standard** modules use a short task phrase (for example
  `configure-storage-accounts`).

## Folder contents

```
learn-pr/<product>/<module-folder-name>/
├── index.yml                     # Module definition + metadata + unit list
├── 1-introduction.yml            # Unit definition (references the .md)
├── 2-<slug>.yml                  # Content unit
├── 3-<slug>.yml                  # Content unit
├── ...                           # More content units
├── <n>-knowledge-check.yml       # Knowledge check (YAML ONLY — no .md)
├── <n+1>-summary.yml             # Summary unit
├── includes/                     # Markdown content for every unit EXCEPT KC
│   ├── 1-introduction.md
│   ├── 2-<slug>.md
│   ├── 3-<slug>.md
│   ├── ...
│   └── <n+1>-summary.md
└── media/                        # Images, video thumbnails, diagrams
```

Key rules:

- **Every unit has a `.yml`** in the module root, numbered in display order.
- **Every unit except the knowledge check has a matching `.md`** in `includes/`.
  The knowledge check's questions live entirely in its `.yml`.
- Unit `.yml` and its `.md` share the same `<n>-<slug>` stem.
- `media/` holds binary assets. Reference them from a unit's Markdown (which
  lives in `includes/`) with a relative path that climbs out of `includes/`:
  `![Alt text](../media/diagram.png)`.

## UID conventions

UIDs are globally unique identifiers used to link modules, units, badges, and
learning paths. **The UID does not include the product folder name.**

- **Module UID** (in `index.yml`): `learn.<module-folder-name>`
  - Example: `learn.intro-to-azure-cloud-shell` (note: no `.azure` segment)
  - Some teams insert a publisher segment, e.g. `learn.wwl.<module-folder-name>`.
    Match the convention used by existing modules in the same `<product>` folder.
- **Unit UID** (in each unit `.yml`, and listed under `units:` in `index.yml`):
  `<module-uid>.<unit-slug>`
  - Example: `learn.intro-to-azure-cloud-shell.introduction`
- **Badge UID** (in `index.yml` `badge:`): `<module-uid>.badge`

The `units:` list in `index.yml` must:

- list unit UIDs in the exact display order, and
- match, one-to-one, the unit `.yml` files in the folder.

## File naming

- Lowercase, kebab-case, ASCII.
- Prefix with the ordinal that matches display order: `1-`, `2-`, …
- Keep the `.yml` stem and the `includes/*.md` stem identical.
- Standard unit slugs: `introduction`, descriptive content slugs,
  `knowledge-check`, `summary`. (Standard modules may also include
  `exercise-<slug>` units.)

## YAML mime headers

The first line of each YAML file declares its type:

- `index.yml` → `### YamlMime:Module`
- unit `.yml` → `### YamlMime:ModuleUnit`

## Module type

`index.yml` `metadata:` includes a `moduleType` field that identifies the
instructional-design pattern:

- **Introduction to** modules → `moduleType: introduction`
- **Standard** modules → `moduleType: standard`

## Icon / badge asset

`index.yml` references an `iconUrl` for the achievement badge. The slug often
spells the title out in full and can differ from the module folder name — for
example the folder `intro-to-azure-cloud-shell` uses
`iconUrl: /training/achievements/introduction-to-azure-cloud-shell.svg`. The
author/Learn team supplies the actual badge SVG; leave the path as a `TODO:` if
the asset does not yet exist.
