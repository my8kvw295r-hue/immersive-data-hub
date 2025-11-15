# Creative Directors for Immersive Media – Dataset README (Pilot Version)

This dataset profiles Creative Directors working in immersive media, including fulldome, XR, large-scale installations, mixed reality stages and destination storytelling. It collects structured metadata for comparative analysis, content strategy, team formation and educational design.

All entries follow the ontological framework described in ../../ontology.md.

---

## Purpose

The dataset describes professional creative leadership in immersive media. It identifies individuals whose work, roles, outputs and contexts reveal the competencies required to direct immersive experiences at professional scale.

The goal is to support:

* identifying creative leadership for immersive projects
* mapping international practice across regions and venue types
* analysing trends in immersive creative direction
* deriving skills for the Skill Taxonomy dataset
* supporting educational and institutional frameworks for immersive media
* enabling agent-based matching between destinations, investors and creative teams

---

## Ontology context

Within the Martin Sambauer Ontology for Immersive Data Systems, this dataset represents the "people and roles" layer.

It connects to:

* **Skill Taxonomy for Immersive Creative Roles** (skills derived from real directors)
* **Immersive Destination Analysis** (destinations where their work appears)
* **Immersive Qualities** (future dataset on perceptual structures)
* **Investor Datasets** (future cross-analysis for project–talent matching)

Each creative director acts as a node linking projects, destinations, venues, skills and media types.

---

## Dataset structure

Each entry in `creative_directors.json` contains the following high-level blocks:

* **identity**

  * id, name, nationality, base city

* **professional_profile**

  * role titles, years active, primary media types

* **immersive_specialisation**

  * fulldome, XR, mixed reality, architectural media, planetarium shows, experience design

* **notable_projects**

  * key works, year, venue, media type, collaborators

* **venues_and_festivals**

  * institutions, festivals, domes, museums, labs

* **skills_reference**

  * which parts of the Skill Taxonomy their work contributes to

* **education_and_background** (optional)

* **sources**

  * URLs, publications, institutional pages

---

## Key results

Key results are not stored statically in this README.
They depend on the current content of the dataset and evolve as new directors are added.

To generate up-to-date insights, summaries or comparisons, load the JSON into an analysis notebook or an LLM and request a profile or analysis.

Typical dynamic insights include:

* distribution of directors across venue types (fulldome, XR, etc.)
* geographic clustering of immersive creative leadership
* project–venue–director triads
* contribution to the Skill Taxonomy dataset
* frequency of roles and sub-roles
* emerging media types and hybrid forms

---

## Methodology

The dataset is compiled through:

1. **Documentation review**

   * festival catalogues, fulldome show credits, XR installations, museum programmes

2. **Cross-dataset extraction**

   * destinations and venues from Immersive Destination Analysis
   * skills derived via the Skill Taxonomy dataset

3. **Role identification**

   * selecting individuals whose primary function is creative leadership rather than technical execution

4. **Metadata structuring**

   * standardising role titles, media types, venue types and project metadata

5. **Ongoing updates**

   * new directors added over time
   * retroactive updates when new work becomes available

---

## Use cases

This dataset is designed for:

* talent sourcing for immersive productions and destination projects
* benchmarking creative leadership in immersive media
* building curricula and training programmes
* analysing artistic and technical evolution across media formats
* generating articles, trend reports and whitepapers on immersive creative direction
* feeding agent-based systems for director–project matching

---

## Planned extensions

Future iterations will include:

* expanded regional coverage (Asia, Africa, Latin America)
* deeper project metadata (budgets, institutions, technologies)
* richer venue mapping (capacity, formats, hardware)
* crosslinking with immersive qualities and perceptual design patterns
* automated ingestion from festival archives and venue databases

---

## Citation

If you use this dataset, please cite:

Creative Directors for Immersive Media (Pilot Version), curated by Martin Sambauer (martin-sambauer.com). Part of the Immersive Datasets repository. Licensed under CC BY 4.0.
