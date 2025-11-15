# Methodology for the Immersive-Investors Dataset

## Operational rules for humans and AI agents

This methodology defines mandatory rules for creating, updating and validating all entries in the Immersive-Investors dataset. It is written explicitly so that LLMs and automated agents can apply it without hallucination, speculation or structural drift.

The methodology applies to all entities in the dataset:

* investors
* institutions
* projects
* policies
* people
* cross-links between them

---

## 1. Core principles

### 1.1 No fabricated data

Agents must never invent:

* investors
* company names
* project names
* people
* budgets
* dates
* policies
* ownership structures
* countries
* affiliations
* roles

Only information that is explicitly present in source material may be added.

### 1.2 No assumptions

If a source implies something but does not explicitly state it:

* do not include it
* do not guess
* do not extrapolate

If a field cannot be filled with certain data, set:

```json
"value": null,
"certainty": "unknown"
```

### 1.3 Mandatory source requirement

Every entity requires:

* at least one URL source
* or a citation pointing to official documentation

If no valid source can be found → the entry must not be created.

### 1.4 No duplicates

Before adding a new entity:

1. Agents must check if an entity with identical or nearly identical identity already exists.
2. Use fuzzy matching on:

   * canonical name
   * aliases
   * website domains
   * known abbreviations

If an entity exists → update it instead of creating a new one.

### 1.5 Stable IDs

IDs follow a strict pattern to maintain consistency:

* Investors: `INV_xxxx`
* Institutions: `INS_xxxx`
* Projects: `PRJ_xxxx`
* Policies: `POL_xxxx`
* People: `PEO_xxxx`

IDs must never be reused, even if an entry is removed.

---

## 2. Required structure for each entity

All entities must follow the schema defined in `schema.json`. Agents must not add new fields unless explicitly instructed.

### 2.1 Required fields for investors

* `id` (stable ID)
* `name`
* `category` (sovereign fund, private equity, family office, corporate, etc.)
* `country`
* `ownership_structure`
* `fund_scale` (if documented; otherwise null)
* `immersive_investment_profile`
* `geographic_focus`
* `instruments`
* `projects_linked`
* `sources`

### 2.2 Required fields for institutions

* `id`
* `name`
* `country`
* `type` (ministry, cultural authority, tourism board, etc.)
* `policies_enabled`
* `projects_enabled`
* `sources`

### 2.3 Required fields for projects

* `id`
* `title`
* `description`
* `country`
* `investors_involved`
* `institutions_involved`
* `immersive_components`
* `sources`

### 2.4 Required fields for policies

* `id`
* `policy_name`
* `country`
* `description`
* `strategic_relevance`
* `institutions_linked`
* `projects_enabled`
* `sources`

### 2.5 Required fields for people

* `id`
* `full_name`
* `role`
* `organisation`
* `country`
* `sectors` (tourism, culture, entertainment, investment, etc.)
* `projects_linked`
* `sources`

---

## 3. Rules for cross-linking

Cross-links must only be created if a source explicitly states a relationship.

### 3.1 Valid relationships

* investor → project (funding or ownership documented)
* institution → project (oversight, enabling, commissioning)
* policy → project (explicitly stated connection)
* person → investor/institution/project (role explicitly documented)

### 3.2 Invalid relationships

Agents must not infer:

* investment links from general thematic alignment
* personal links from press photos
* institutional links from geographic proximity

---

## 4. Versioning rules

Every dataset update must increment:

* `version_major` (only when schema changes)
* `version_minor` (when fields are added or structural changes occur)
* `version_patch` (when new entries are added or corrected)

Agents must update the timestamp in `dataset_metadata`.

---

## 5. Validation rules for LLMs and agents

Before writing any entry, the agent must follow this validation sequence:

1. Check schema compliance – all required fields present.
2. Check for duplicates – fuzzy name matching.
3. Check source validity – at least one reliable URL.
4. Check factual certainty – no invented values.
5. Check cross-links – only if explicitly documented.
6. Write entry to dataset – using the stable ID format.

If any step fails → the agent must not create the entry.

---

## 6. Rules for automated extensions

Automated agents may extend the dataset, but must obey:

* no hallucinated content
* no speculative investors or projects
* no unverifiable budget figures
* no new fields outside the schema
* no rewriting or deletion of existing sourced content
* all new entries must include valid sources

---

## 7. Notes for human collaborators

Human contributors may add commentary, additional sources or structural improvements, but must respect:

* schema integrity
* ID stability
* source-based documentation
* no duplication

---

## 8. Purpose of this methodology

This methodology ensures that the Immersive-Investors dataset remains:

* reliable
* auditable
* expandable
* compatible with automated agents
* safe from hallucinations
* consistent across regions and updates

It is designed to support long-term integration into the broader immersive data ecosystem curated by Martin Sambauer.
