## Methodology for the “Creative Directors in Immersive Media – Global Dataset (1950–2025)”

This document describes how the dataset `creative_directors_global.json` was curated, which decisions shaped its scope, and how entries can be reproduced or extended.

The methodology is designed to be transparent and lightweight, so that future contributors can keep the dataset coherent over time.

---

## 1. Definition of Scope (1950–2025)

The dataset documents individuals whose work substantially contributes to immersive media, including but not limited to:

- immersive cinema and expanded cinema
- media art and interactive installations
- fulldome and large-format storytelling
- VR / XR and spatial cinema
- LED stages, domes and immersive arenas
- corporate and brand-related immersive experiences

The temporal scope is 1950–2025. Earlier avant-garde work is included when it shows a clear lineage toward large-scale media environments, multiscreen experiments or proto-immersive formats.

Only natural persons are listed; companies, studios and collectives appear as `affiliations`, not as primary entries.

---

## 2. Establishing Conceptual Clusters

To make the dataset analytically useful, each entry is mapped to one or more conceptual clusters via the `clusters` field:

- `analog_media_art_pioneers`
- `digital_interactive_pioneers`
- `immersive_installations`
- `fulldome_large_format`
- `vr_xr_creators`
- `live_immersive_stages`
- `corporate_brand_immersive`

These clusters are intentionally overlapping. Many individuals span several areas over their careers (for example, moving from media art into fulldome storytelling or from corporate experience design into live immersive stages).

The clusters are not value judgements or rankings. They exist to support comparative analysis and to make it easier to filter the dataset for specific research questions.

---

## 3. Selection of Individuals

Inclusion is based on publicly verifiable contributions to immersive media. Typical indicators are:

- direction or creative direction of an immersive show, film, installation or experience
- sustained authorship in immersive formats (e.g. multiple works in VR, fulldome, immersive theatre, LED stages)
- recognized authorship in festivals, institutions, museums, planetariums or major venues
- clear presence in professional discourse (interviews, retrospectives, critical writing)

Each person must be identifiable as a natural person with a real-world practice. Pseudonyms and artist names are allowed when they are the main public identity.

The dataset is explicitly not exhaustive and not a ranking. It is a curated research corpus that will grow and shift over time.

---

## 4. Data Collection and Normalization

The initial population of the dataset draws on:

- festival catalogues and programmes (film, media art, VR / XR, fulldome, immersive theatre)
- museum and institution archives
- planetarium and dome venue programme histories
- conference records and industry events
- press articles, interviews and artist profiles
- studio and personal websites

For each candidate, the following fields are collected where possible:

- `name`
- `country`
- `birth_year` (if verifiable)
- `roles`
- `focus_areas`
- `notable_works`
- `affiliations`
- `clusters`
- `links`
- `sources`

Names are stored in a single `name` field following the dominant public form (no strict family-name / given-name split). Years of birth are only included when present in reliable public sources.

All data is transformed into normalized JSON according to `creative_directors_global.schema.json`:

- consistent types (arrays vs. scalars)
- ISO dates where applicable
- URI-formatted links
- lower_snake_case field names

---

## 5. Source Documentation

Every entry must have at least one verifiable source, stored in the `sources` array:

```json
"sources": [
  {
    "label": "Venice Immersive 2023 – Official Selection",
    "url": "https://example-festival.org/programme/immersive-2023"
  }
]
```

Typical sources include:

- festival programmes and catalogues
- museum and institutional collection pages
- official studio or project websites
- interviews and press coverage from reputable outlets
- academic profiles and research institution pages

If a statement about an individual cannot be backed by a stable external source, it should not be included or must be clearly marked in `notes`.

---

## 6. Identifier Strategy

Each entry receives a stable, human-readable ID in the field `id`:

- prefix: `cdim_`
- numeric suffix: zero-padded, sequential (`cdim_0001`, `cdim_0002`, …)

IDs are stable once assigned and must not be reused, even if an entry is removed at a later stage. Corrections to an entry keep the same ID.

A simple registry (for example the index of the JSON file or a separate change log) can be used to prevent accidental reuse.

---

## 7. Duplicate Handling and Merging

Duplicates can occur when:

- the same person appears under different spellings or transliterations
- festival and institutional records use different variants of the name
- collaborative collectives are misinterpreted as individuals

When duplicates are detected:

1. Decide on the canonical `name` based on the most authoritative source.
2. Merge `roles`, `focus_areas`, `notable_works`, `affiliations`, `clusters`, `links` and `sources`.
3. Keep the earliest assigned `id` and mark the resolution in `notes` if useful.
4. Remove the redundant entry from the dataset rather than keeping multiple IDs for the same person.

---

## 8. Quality Checks and Validation

Before publishing a new version of `creative_directors_global.json`:

- validate the file against `creative_directors_global.schema.json`
- ensure that:
  - all `id` values are unique
  - every entry has at least one cluster in `clusters`
  - every entry has at least one element in `sources`
  - URLs in `links` and `sources` are syntactically valid
- run a simple spell check on `name`, `roles` and `focus_areas` to catch obvious typos

Automated validation can be done with any JSON Schema validator (CLI tools, Python, Node etc.).

---

## 9. Versioning and Changelog

Changes to the dataset are tracked in `changelog.md` with semantic versioning:

- MAJOR – structural changes to the schema or field definitions
- MINOR – new individuals, clusters, or substantial metadata extensions
- PATCH – corrections, typo fixes, updated links, additional sources

Each changelog entry should include:

- version number
- date
- short summary (1–3 bullet points)
- optional notes on methodology-relevant decisions

---

## 10. Limitations and Future Work

The dataset is shaped by:

- language bias (emphasis on sources available in languages the curator can read)
- festival and institutional visibility (independent scenes are harder to document)
- uneven historical coverage (recent years often have denser documentation)

Future extensions may include:

- more fine-grained regional tagging
- explicit links to works datasets (one-to-many relationship between creators and works)
- integration with other immersive datasets (venues, keywords, market participants)

Researchers and practitioners are invited to propose additions and corrections via pull requests or issue tracking in the main repository.
