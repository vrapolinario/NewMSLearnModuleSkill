# Required & recommended metadata for training modules

Every module `index.yml` and every unit `.yml` carries a `metadata:` block.
Microsoft Learn's content build **requires** a core set of fields; missing or
invalid values fail validation.

## Required metadata fields (every `metadata:` block)

| Field | Description | Notes |
| --- | --- | --- |
| `title` | Page title for SEO/browser tab. | 60 chars or fewer is ideal. Can differ from the visible module/unit `title`. |
| `description` | Summary of the content for search. | 75–300 characters. Distinct from the module `summary`. |
| `ms.date` | Date last updated, `MM/DD/YYYY`. | Use today's date when drafting. |
| `author` | The author's **GitHub alias**. | The requesting user. No `@`. |
| `ms.author` | The author's **Microsoft alias**. | The part before `@microsoft.com`. |
| `ms.topic` | Content type. | Use `module` in `index.yml`; `unit` in unit files. |
| `ms.service` **or** `ms.product` | The product/service taxonomy value. | Exactly one is required. Example: `ms.service: azure-cloud-shell`. |

> The author identity (`author` + `ms.author`) is mandatory and must be the
> person requesting the module. Confirm both aliases before writing.

## Additional `index.yml` `metadata:` fields

| Field | Required | Description |
| --- | --- | --- |
| `moduleType` | Yes | The pattern: `introduction` for "Introduction to" modules, `standard` for Standard modules. |
| `ms.custom` | Optional | Team/tracking tag, e.g. `team=cloud_advocates`. |

## Module-level fields (in `index.yml`, outside `metadata:`)

| Field | Required | Description |
| --- | --- | --- |
| `uid` | Yes | `learn.<module-folder-name>` (no product segment; some teams use `learn.<publisher>.<module-folder-name>`). |
| `title` | Yes | Visible module title. |
| `summary` | Yes | 1–3 sentences describing the module (shown in catalog). |
| `abstract` | Yes | Bulleted "In this module, you will:" learning objectives. |
| `prerequisites` | Yes | Bulleted prerequisites, or "None." |
| `iconUrl` | Yes | Badge/icon path, e.g. `/training/achievements/<badge-slug>.svg`. The slug may spell the title out in full and differ from the folder name. |
| `levels` | Yes | One or more of `beginner`, `intermediate`, `advanced`. |
| `roles` | Yes | One or more audience roles (see list below). |
| `products` | Yes | One or more product taxonomy slugs (e.g. `azure`). |
| `subjects` | Recommended | Subject taxonomy slug(s) (e.g. `cloud-computing`). |
| `units` | Yes | Ordered list of unit UIDs. |
| `badge` | Yes | `uid: <module-uid>.badge`. |

## Unit-level fields (in each unit `.yml`, outside `metadata:`)

| Field | Required | Description |
| --- | --- | --- |
| `uid` | Yes | `<module-uid>.<unit-slug>`. |
| `title` | Yes | Visible unit title. |
| `durationInMinutes` | Yes | Estimated minutes (integer). |
| `content` | Yes* | `[!include[](includes/<n>-<slug>.md)]`. *Omit for the knowledge-check unit, which uses `quiz:` instead. |
| `quiz` | KC only | Present only on the knowledge-check unit. |

## Common allowed values

**`levels`**: `beginner`, `intermediate`, `advanced`.

**`roles`** (choose the closest; not exhaustive): `administrator`,
`ai-engineer`, `business-analyst`, `business-owner`, `business-user`,
`data-analyst`, `data-engineer`, `data-scientist`, `database-administrator`,
`developer`, `devops-engineer`, `functional-consultant`, `maker`,
`network-engineer`, `privacy-manager`, `risk-practitioner`,
`security-engineer`, `solution-architect`, `startup-founder`, `student`,
`support-engineer`, `technology-manager`.

**`products`** (examples): `azure`, `azure-cloud-shell`, `azure-portal`,
`azure-storage`, `azure-functions`, `m365`, `dynamics-365`, `github`,
`dotnet`, `power-bi`, `power-apps`, `microsoft-copilot`. Use the slug that
matches the technology.

**`subjects`** (examples): `cloud-computing`, `artificial-intelligence`,
`data-management`, `development-tools`, `security`, `devops`,
`infrastructure`, `productivity`.

> Taxonomy slugs evolve. If unsure of an exact slug, pick the nearest match and
> add a `TODO:` note for the author to confirm against the current allowed-values
> list before publishing.

## Date

Always set `ms.date` to the drafting date in `MM/DD/YYYY` format. Update it on
any later edit.
