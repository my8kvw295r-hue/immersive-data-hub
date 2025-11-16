# Methodology for the Immersive-Investors Dataset

## Operational rules for humans and AI agents

This methodology defines mandatory rules for creating, updating and validating all entries in the Immersive-Investors dataset.

It is written for:

* human curators and researchers
* AI agents that extend or cross-link the dataset
* downstream applications (dashboards, analysis tools, LLM-based systems)

Any agent that writes to or reasons over this dataset must follow this methodology exactly. If a model cannot follow these rules, it must not attempt to update the dataset or apply it without hallucination, speculation or structural drift.

The methodology applies to all entities in the dataset:

* investors
* institutions
* projects
* policies
* people
* cross-links between them

## 1. Core principles

### 1.1 No fabricated data

All entries must be based on verifiable, public sources:

* official websites
* annual reports and financial statements
* strategy documents and presentations
* press releases
* reputable news media
* conference materials and official speeches

If a value cannot be sourced, it must be left null or omitted, not invented.

### 1.2 No assumptions

Curators and AI agents may not:

* infer fund sizes from generic labels such as “large fund”
* guess geographic focus from a country name alone
* assume immersive investments just because an investor is active in tourism, culture or technology
* treat marketing slogans as hard evidence of an immersive portfolio

Whenever uncertainty exists, the correct behaviour is:

* leave the field empty or set to “unknown”
* add a short explanatory note in the `notes` field
* include the sources that show why the value is unknown or ambiguous

### 1.3 Mandatory source requirement

Every investor, institution, project, policy and person must have at least one concrete source attached.

The `sources` field is mandatory and must list:

* URL(s)
* document titles where possible
* short comment if the source is a PDF, long report or offline document

If no sources can be identified, the entity must not be created.

### 1.4 No duplicates

Each entity must have a stable ID and must not be duplicated under multiple names.

* If an investor appears under different brand names or abbreviations, they must be merged into one canonical investor with aliases captured in the description or notes.
* If two entries describe the same project under slightly different labels, curators must consolidate them.

AI agents must not create new entities if a matching entity already exists under a different spelling.

### 1.5 Stable IDs

IDs must be:

* stable across versions
* human-readable where practical
* unique within the dataset

Examples:

* `INV_PIF_SAUDI_ARABIA`
* `INST_MIRAL_ABU_DHABI`
* `PROJ_QIDDIYA_CITY_SAUDI_ARABIA`
* `POL_SAUDI_VISION_2030`
* `PERSON_YASIR_AL_RUMAYYAN`

IDs must not be recycled. If an entity is deprecated, it is marked as such in its notes, but the ID remains reserved.

## 2. Required structure for each entity

This section describes the minimal fields required for each entity type. The JSON schema in `schema.json` defines the full machine-readable structure. The methodology focuses on conceptual obligations.

### 2.1 Required fields for investors

* `id` (stable ID)
* `name`
* `category` (sovereign fund, private equity, family office, corporate, etc.)
* `country`
* `ownership_structure`
* `fund_scale` (if documented; otherwise null)
* `immersive_investment_profile`
* `geographic_focus`
* `project_location_profile` (conceptual focus such as global_south, emerging_markets, offshore_islands)
* `immersive_modalities_focus` (fulldome, LBE, XR platforms, media facades, etc.)
* `instruments`
* `projects_linked`
* `sources`

The `immersive_investment_profile` must explicitly state whether the investor has:

* no documented immersive activity
* early and experimental involvement
* an emerging portfolio
* an established, long-term immersive portfolio

`project_location_profile` and `geographic_focus` are complementary:

* `geographic_focus` describes concrete regions and countries referenced in sources.
* `project_location_profile` captures higher-level patterns such as “global_south”, “emerging_markets” or “offshore_islands” that can be used for scenario analysis. It must only be populated if there is clear evidence (for example repeated investments in Global-South destinations, island resorts or coastal hubs).

`immersive_modalities_focus` describes which immersive modalities the investor demonstrably finances. It must be based on projects and documented strategies, not speculation.

### 2.2 Required fields for institutions

* `id`
* `name`
* `country`
* `institution_type` (ministry, agency, development company, holding, etc.)
* `description`
* `linked_investors`
* `linked_policies`
* `sources`

Institutions often act as owners or operators of projects. They are not investors by default; they only appear in `investors` if they directly deploy investment capital.

### 2.3 Required fields for projects

* `id`
* `title`
* `description`
* `country`
* `investors_involved`
* `institutions_involved`
* `immersive_components`
* `global_south_flag`
* `offshore_flag`
* `sources`

#### 2.3.1 Global South and offshore flags

For each new project, curators must explicitly set:

* `global_south_flag` to true if the project is located in, or primarily targets, Global South contexts as defined in this repository (see README for the current working definition).  
* `offshore_flag` to true if the project is located on an island, artificial island or offshore zone (for example an island resort, offshore special economic zone or coastal island city).

These flags are not subjective branding. They must be derived from documented geography (country, region, legal status) and, where ambiguous, the safer choice is `false` with an explanatory note in the project `notes` field.

Typical immersive components include:

* domes and fulldome theatres
* XR parks and mixed-reality venues
* immersive exhibitions and media districts
* immersive museum or science-centre installations
* large-scale media facades and LED domes

### 2.4 Required fields for policies

* `id`
* `policy_name`
* `country`
* `description`
* `strategic_relevance`
* `institutions_responsible`
* `sources`

Policies include:

* national vision documents
* tourism and cultural strategies
* dedicated creative industries and immersive media strategies
* science and education policies that explicitly reference immersive infrastructures

### 2.5 Required fields for people

* `id`
* `name`
* `role`
* `organisation`
* `country`
* `responsibility_area`
* `sources`

Only people with direct relevance for immersive investments should be included:

* heads of sovereign funds
* ministers and agency heads responsible for relevant portfolios
* chief experience/tourism/culture officers
* directors of major immersive destination projects

## 3. Rules for cross-linking

### 3.1 Valid relationships

Valid cross-links include:

* investor → project (funding, co-funding)
* investor → institution (ownership, governance, mandates)
* investor → policy (explicit mention or mandate)
* institution → project (operator, developer, owner)
* policy → project (flagship project, named pilot)
* person → investor/institution/project (formal leadership role)

Cross-links must:

* be supported by sources
* indicate the nature of the relationship (e.g. “anchor investor”, “project owner”, “mandated in Vision 2030”)
* avoid overlinking; links must remain meaningful and focused

### 3.2 Invalid relationships

Invalid or discouraged links include:

* speculative “influence” relationships without explicit evidence
* generic mentions in speeches that do not establish a structural link
* social-media-only mentions without corroborating documentation

AI agents must not create or suggest cross-links without a clear chain of evidence.

## 4. Versioning rules

* All changes to the dataset must increment the semantic version in `dataset_metadata.version`.
* Minor version increments (`0.1.0` → `0.2.0`) cover:
  * new entities
  * added cross-links
  * non-breaking schema extensions
* Patch version increments (`0.1.0` → `0.1.1`) cover:
  * corrections
  * typo fixes
  * better source annotation

Breaking schema changes require a major version change (`0.x` → `1.0.0`) and careful migration notes.

## 5. Validation rules for LLMs and agents

AI agents extending the dataset must:

1. Parse `schema.json` and respect all required fields and types.
2. Reject any operation that would:
   * violate required fields
   * introduce null where a value is mandatory
   * add entities without sources
3. Validate URLs and basic source sanity (e.g. no clearly spammy or unrelated links).

When in doubt, agents must:

* log the ambiguity in a note field
* leave fields unset
* prefer under-specification to hallucination

## 6. Rules for automated extensions

Automated agents may:

* propose new investors, institutions, projects, policies and people
* enrich existing entities with additional sourced attributes
* propose cross-links

They must not:

* infer fund sizes without explicit numbers
* generalise from single examples to “global” patterns
* label a project or investor as “Global South” or “offshore” without geographic evidence

All automatically proposed entities and changes must be:

* clearly marked in change logs
* reviewed by a human curator before being merged into canonical files

## 7. Notes for human collaborators

Human collaborators should:

* treat this dataset as a living research artefact
* document reasoning in `notes` fields where helpful
* avoid converting marketing language 1:1 into analytical claims
* always preserve the distinction between:
  * what is explicitly stated in sources
  * what is carefully inferred
  * what remains unknown

## 8. Purpose of this methodology

The methodology exists to:

* keep the dataset analytically useful and trustworthy
* allow reproducible research
* provide a solid foundation for AI systems that rely on this data
* support scenario work for immersive investments in destinations, including Global-South and offshore island contexts

It must be updated whenever:

* the schema changes in a non-trivial way
* new entity types or cross-link logics are introduced
* the conceptual understanding of immersive investment evolves

## 7. Temporal validity and review rules

The dataset is a snapshot at a given time and must include:

* `dataset_metadata.snapshot_date`
* `dataset_metadata.last_reviewed`

Each entity should, where possible, include:

* `data_valid_as_of`
* `last_checked`

Curators must:

* prioritise updating entities with time-sensitive information (e.g. leadership roles, portfolio compositions)
* clearly mark outdated or superseded information

## 8. Provenance and source discipline

Provenance is central. For each entity:

* list all major sources
* prefer primary sources (official sites, documents) over secondary coverage
* if multiple sources conflict, describe the conflict in the notes field and choose the more conservative interpretation

This methodology is itself versioned and aligned with the JSON schema. When the schema adds new conceptual layers (for example Global-South and offshore flags or new immersive modalities), the methodology must be updated in lockstep.
