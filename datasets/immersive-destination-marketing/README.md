# Immersive Destination Marketing – Dataset README (Pilot Version)

This dataset documents immersive destination marketing outputs: campaigns, productions, fulldome and XR experiences, large-scale media installations, narrative tourism assets and experiential communication created to position destinations in global competition.

It provides structured metadata on how destinations communicate themselves through immersive formats and acts as a bridge between destination identity, creative direction and investor interest.

All entries follow the ontological framework described in ../../ontology.md.

---

## Purpose

The goal of this dataset is to map how destinations use immersive media to shape tourism flows, cultural identity, soft power, regional branding and experiential positioning.

It supports:

* identifying immersive media outputs used in destination marketing
* analysing common narrative structures across regions and destination types
* connecting destinations with creative directors, studios and production teams
* mapping which media types (fulldome, 360°, XR, architectural media) dominate tourism communication
* deriving skills for the Skill Taxonomy through documented outputs
* preparing stacked datasets that combine destinations, investors and creative talent

This dataset is closely tied to the Immersive Destination Analysis dataset, but focuses on *outputs* rather than structural indicators.

---

## Ontology context

In the Martin Sambauer Ontology for Immersive Data Systems, this dataset represents the "media outputs" layer.

It connects to:

* **Immersive Destination Analysis** (destination-level identity, tourism flows, economic context)
* **Creative Directors for Immersive Media** (authors of the immersive outputs)
* **Skill Taxonomy for Immersive Creative Roles** (skills derived from these outputs)
* **Investor Datasets** (to match immersive projects with funding appetites)

Destinations are narrative identities; this dataset documents the media artefacts that construct these identities.

---

## Dataset structure

Each entry in `immersive_destination_marketing.json` contains the following blocks:

* **identity**

  * id, title of the output, short description, year

* **destination_reference**

  * destination id, destination name, region, links to Immersive Destination Analysis

* **media_format**

  * fulldome, 360°, XR, VR, mixed reality stage, architectural media, projection mapping etc.

* **storytelling_profile**

  * narrative themes (nature, heritage, futurism, spirituality, sustainability)
  * structural patterns (journey, transformation, encounter, spectacle)

* **production_info**

  * studio, creative director, country of production
  * collaborators, technical stack (camera type, rendering pipeline, audio format)

* **exhibition_context**

  * venue type (planetarium, fulldome, museum, XR venue, event stage)
  * festivals or premieres

* **strategic_positioning**

  * tourism segment addressed (luxury, adventure, heritage, eco, educational)
  * soft-power angle (innovation, cultural revival, environmental stewardship)

* **sources**

  * URLs, videos, press releases, festival listings

---

## Key results

Key results evolve as the dataset grows, but this section also includes stable interpretative insights that remain valid regardless of how many entries the dataset will eventually contain.

### Dynamic results (generated on demand)

For up-to-date quantitative insights (counts, dominance of formats, regional weightings, etc.) load the JSON into an analysis notebook or LLM.

### Stable interpretative insights (conceptual reading)

These insights remain meaningful even as the dataset expands:

1. **Immersive destination marketing is narrative infrastructure.**
   Destinations do not simply advertise themselves; they construct narrative identities through immersive media. The dataset makes this visible across fulldome films, XR experiences, and architectural media installations.

2. **Most immersive outputs translate geographic reality into experiential arcs.**
   Regardless of the destination, productions repeatedly follow transformational structures: journey → encounter → revelation. This reflects a global grammar of place-based storytelling.

3. **Immersive media act as soft-power multipliers.**
   Several outputs (especially from MENA and Asia) function less as tourism promotion and more as cultural positioning tools. Immersion becomes a form of geopolitical signalling.

4. **Creative direction, destination identity and investment logic converge.**
   The dataset shows that many immersive outputs sit at the intersection of creative direction, tourism strategy, real-estate development and investor expectations — not purely in the cultural domain.

5. **Fulldome and XR formats dominate early-stage immersive destination narratives.**
   These formats provide the clearest pipeline from physical place → symbolic narrative → immersive experience. Architectural media appear where budgets and urban contexts allow for large-scale projection.

6. **The dataset helps identify narrative gaps.**
   By comparing outputs, it becomes visible where a destination relies heavily on tradition, nature, futurism or spectacle — and where untapped narrative potential exists.

---

## Methodology

1. **Identification of outputs**
   Immersive tourism films, fulldome shows, XR experiences and media installations that position destinations.

2. **Metadata extraction**

   * venue and festival listings
   * tourism board productions
   * studio portfolios
   * press releases and cultural programme archives

3. **Narrative and structural analysis**

   * identifying recurring themes, motifs and immersive techniques

4. **Crosslinking with other datasets**

   * destination ids from Immersive Destination Analysis
   * creative leadership from Creative Directors dataset
   * skill derivation for the Skill Taxonomy

5. **Standardised schema modelling**
   Ensuring consistent fields for media formats, narrative profiles, venues and production roles.

---

## Use cases

This dataset is intended for:

* analysing how destinations use immersive media to shape global perception
* identifying stylistic or structural patterns in immersive tourism storytelling
* sourcing references for new immersive destination marketing projects
* matching destinations with creative directors and studios
* informing investor outreach where immersive storytelling aligns with soft-power goals
* curriculum development for immersive narrative design

---

## Planned extensions

* structured mapping of destination marketing budgets (where available)
* deeper breakdown of narrative archetypes
* mapping the evolution of immersive formats in tourism campaigns over time
* larger regional coverage (MENA, Southeast Asia, Latin America)
* inclusion of more projection mapping festivals, façade shows and location-based immersive experiences that function as destination narratives

---

## Contributing

The dataset is intentionally open for growth. If you work with immersive destination marketing, projection mapping festivals or location-based immersive experiences, you are invited to extend and refine this dataset.

Typical contributions include:

* adding new immersive campaigns or experiences for specific destinations
* enriching existing entries with missing fields (venues, media formats, narrative themes)
* documenting projection mapping festivals and permanent installations that shape destination identity

Contributions can be made via standard git workflow (fork, branch, commit, pull request) against the immersive-datasets repository.

---

## Citation

If you use this dataset, please cite:

Immersive Destination Marketing (Pilot Version), curated by Martin Sambauer (martin-sambauer.com). Part of the Immersive Datasets repository. Licensed under CC BY 4.0.
