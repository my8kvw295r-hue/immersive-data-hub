Creative Directors in Immersive Media – Global Dataset (1950–2025)

This repository hosts the Creative Directors in Immersive Media – Global Dataset, a machine-readable collection of individuals working in the field of immersive media, immersive events, fulldome cinema, XR, experiential architecture, and large-scale media environments.

The dataset is part of a long-term research project to map the evolution of immersive media creative direction from the 1950s to the present.
It accompanies the article Creative Directors in Immersive Media: A Global Overview (1950–2025) published at:

https://martin-sambauer.com

Purpose of the Dataset

Immersive media has established itself as a global field spanning:

multiscreen and expanded cinema

media art and interactive installations

fulldome and large-format storytelling

VR / XR and spatial cinema

LED stages and immersive arenas

corporate immersive experiences

Yet there has never been a structured, global overview of the individuals who shape this field.

This dataset aims to:

document creative directors, artists, designers and producers working in immersive media

provide a historical arc (1950–2025)

classify individuals across multiple clusters and domains

offer a machine-readable reference for researchers, curators, festivals and institutions

support long-term analysis of trends, technologies and professional roles in immersive media

The dataset is not a ranking and not a complete list. It is an evolving research corpus.

Dataset Structure

All data is stored in:

/datasets/immersive-creative-directors/
    creative_directors_global.json
    creative_directors_global.schema.json  (optional)
    methodology.md
    changelog.md


The main file is:

creative_directors_global.json


It contains an array of entries.
Each entry describes one individual and follows this structure:

{
  "id": "cdim_0001",
  "name": "…",
  "type": "individual",
  "primary_roles": [],
  "domains": [],
  "primary_mediums": [],
  "creative_focus_tags": [],
  "active_years": "",
  "geography": [],
  "clusters": [],
  "focus_summary": "",
  "key_works": [
    {
      "title": "",
      "year": "",
      "venue_or_context": "",
      "notes": ""
    }
  ],
  "influence_level": "foundational | major | emerging",
  "short_bio": "",
  "website": "",
  "references": [
    {
      "title": "",
      "url": "",
      "publisher": "",
      "year": "",
      "notes": ""
    }
  ],
  "notes": null
}

How the Dataset Was Created

The dataset was built through a multi-step curation process:

1. Definition of Scope (1950–2025)

We defined the field based on media history, not on current buzzwords.
Included categories range from early multi-screen avant-garde to contemporary XR stages and immersive brand experiences.

2. Establishing Conceptual Clusters

To classify the diverse field, we created the following clusters:

analog_media_art_pioneers

digital_interactive_pioneers

immersive_installations

fulldome_large_format

vr_xr_creators

live_immersive_stages / large_scale_live_shows

corporate_brand_immersive

Each individual may belong to multiple clusters.

3. Selection of Individuals

The dataset includes:

artists, directors, media creators, designers and producers

whose work primarily involves immersive media

with verifiable public output (festivals, museums, planetariums, venues, publications)

individuals only (no studios as standalone entries)

4. Verification Through Public Sources

Every entry contains at least one real, verifiable reference, such as:

festival catalogues

planetarium and fulldome databases

museum exhibition descriptions

academic or institutional profiles

studio or artist websites

press releases and published interviews

No unverified or anonymous entries were included.

5. JSON Normalization

All entries were normalized to:

consistent field naming

consistent formatting

unique IDs (cdim_0001 → cdim_XXXX)

machine-readable types and arrays

a predictable schema for downstream analysis

6. Duplicate Removal and Replacement

Where individuals appeared twice under different IDs, entries were merged.
Where entries lacked references, they were replaced with new individuals who:

fit the cluster structure

are relevant to immersive media history

have publicly verifiable sources

7. Systemic Integrity Check

Before release, we ensured:

every entry has at least one reference

no duplicated names

no duplicated IDs

all links resolve

all fields conform to the schema

8. Compatibility With Other Datasets

This dataset is designed to interconnect with:

Immersive Market Participants

Immersive Venue and Planetarium Databases

Immersive Keywords Dataset

Together, these datasets form a broader ecosystem map of immersive media.

License

This dataset is released under:

Creative Commons Attribution 4.0 International (CC BY 4.0)
https://creativecommons.org/licenses/by/4.0/

You are free to:

share – copy and redistribute the material in any medium or format

adapt – remix, transform, and build upon the material for any purpose, even commercially

Under the following terms:

attribution – you must give appropriate credit, provide a link to the license, and indicate if changes were made.
Please credit:

“Creative Directors in Immersive Media – Global Dataset (1950–2025), curated by Martin Sambauer – https://martin-sambauer.com”

Versioning

All updates are logged in:

changelog.md


Versioning follows:

MAJOR: structure changes, new schema

MINOR: new individuals added, clusters expanded

PATCH: corrected links, typos, metadata

Contributing

This is a curated research project.
Contributions (corrections, new individuals, references) are welcome via pull request.

Maintainer

Martin Sambauer
Creative Director for Immersive Media
https://martin-sambauer.com
