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

---

## 7. Temporal validity and review rules

1. Dataset-level timestamps

- `dataset_metadata.snapshot_date`  
  The date of the current JSON snapshot. Any consumer should treat this as the minimum date of validity for the file as a whole.

- `dataset_metadata.last_reviewed`  
  The date when a human curator last reviewed the dataset in a structured way (e.g. a curation sprint).

2. Entity-level timestamps

All entities (investors, institutions, projects, policies, people) carry:

- `data_valid_as_of` – the ISO date (YYYY-MM-DD) the entry is considered valid as of.
- `last_checked` – the ISO date when the entry was last manually checked or updated.

Operational rule:

- If `last_checked` is older than 18 months, agents must flag the entity as potentially outdated.
- Automated agents must not silently overwrite timestamps; only explicit curation passes may bump `last_checked`.

3. Time for quantitative fields

For time-sensitive quantitative values (e.g. AUM, fund size) the preferred pattern is:

- `fund_size_overall.amount` (number)
- `fund_size_overall.currency` (e.g. USD)
- `fund_size_overall.as_of_date` (ISO date, precise if available)
- optional `fund_size_overall.as_of_year` (legacy/approximate)

Agents must not infer dates; if a date is unknown, leave the field `null` and document this in the notes.

---

## 8. Provenance and source discipline

The following rules are mandatory:

1. No value without a source

- Every non-null factual value must be supported by at least one external source.
- The entity-level `sources` array must contain the URLs or formal references that justify the values used.

2. No synthesis beyond the sources

- Agents and curators must not invent values that are not clearly supported by the sources.
- If multiple sources disagree, choose the most recent and clearly mark the uncertainty in `notes`.

3. Handling of uncertainty

- If a value cannot be justified from available sources, set it to `null`.
- If there is an approximate but not exact value (e.g. "about $900bn AUM"), choose a reasonable numeric approximation and explain the choice in `fund_size_overall.note` or the entity `notes`.

These rules ensure that downstream users can audit any field by going back to at least one documented source. Field-level provenance (per-field `source_ids`) may be introduced later, but for the current version entity-level provenance is the minimum requirement.

