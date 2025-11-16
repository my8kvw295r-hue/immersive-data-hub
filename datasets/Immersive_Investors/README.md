## Immersive Investors – global capital for immersive infrastructures and experiences

Immersive Investors is a curated data repository mapping investors, funds, institutions and policies that support immersive infrastructures and experiences worldwide.

The repository is global in scope, but the pilot phase starts with a focus on the Arab region (GCC and selected wider MENA countries) where giga-projects, sovereign funds and destination initiatives play a leading role in immersive destination projects.

Immersive Investors is maintained by Creative Director Martin Sambauer (martin-sambauer.com).

---

## Purpose and scope

The goal of this repository is to describe how capital, policy and immersive infrastructures intersect, with a focus on:

- sovereign wealth funds and tourism/entertainment development funds  
- private equity, family offices and corporate vehicles investing in immersive projects  
- ministries, cultural bodies and vision programs that frame these investments  
- concrete projects and venues (domes, XR parks, media districts, exhibition clusters) funded or enabled by these actors  
- key people responsible for strategic decisions in immersive-related portfolios  

The repository is intended to support:

- destinations and venues searching for immersive-relevant investors  
- analysis of soft-power and tourism strategies in immersive infrastructures  
- cross-analysis with immersive destination, skill and creative-director datasets  
- AI agents that match destinations, investors and creative teams  
- journalism, research and strategic writing about immersive economics

A key design goal is to support scenario work for immersive destinations in the Global South, including offshore and island projects. To make this analysable, the schema introduces explicit flags and profiles for Global-South and offshore locations at project level, and conceptual `project_location_profile` fields at investor level. These additions allow curators and AI agents to ask targeted questions such as: "which investors already back Global-South coastal or island destinations with immersive content?"

Even though the pilot starts in the Arab region, the structure is global and designed to accommodate investors from all regions over time.

---

## Ontology and conceptual background

Immersive Investors is aligned with the Martin Sambauer Ontology for Immersive Data Systems.

In this ontology, immersive investment is not reduced to “who funds what”, but is understood as:

- a soft-power instrument  
- a tourism and place-making tool  
- a structuring force for cultural and entertainment ecosystems  
- a driver of new perceptual architectures in cities and destinations  

Investors, institutions, projects, destinations and people are modelled as connected entities in a larger immersive knowledge graph.

A dialectical view of immersive economics is central: immersive infrastructures are seen as sites where economic and geopolitical logics become visible, and where tensions (for example between local communities and global tourism, or between infrastructure and nature, authenticity vs staging) into visible, discussable forms.

This conceptual layer is what makes the data usable for analysis, journalism, LLMs and agents rather than just a list of names.

---

## Repository structure

The repository is organised as:

- `immersive_investors_global_v01.json`  
  Main dataset file, containing investors, institutions, projects, policies, people and meta-instructions.

- `schema.json`  
  JSON Schema describing the allowed structure and values.

- `meta/`  
  Methodology, notes on curation, potential extensions.

The structure is deliberately simple so that it can be loaded into notebooks, data warehouses and LLM-based tools without friction.

---

## Core dataset structure

The main JSON file `immersive_investors_global_v01.json` is designed with these top-level keys:

- `dataset_metadata`  
  Basic information: title, version, description, scope, license, author, timestamps.

- `investors`  
  Array of investor objects describing:

  - investor identity (name, category, country, HQ city)  
  - ownership and governance (sovereign fund, state fund, private equity, family office, corporate)  
  - overall fund scale (where documented)  
  - immersive investment profile:
    - whether an immersive portfolio exists  
    - estimated allocation and share of capital going into immersive projects  
    - portfolio maturity (very_new, emerging, established, long_term)  
    - preferred stages (seed, early_stage, growth, infrastructure, late-stage content, venue development)  
    - typical ticket size ranges  
  - instruments (equity, project finance, PPP, grants, mixed)  
  - thematic focus (tourism, culture, sports, smart city, metaverse, museums, creative industries)  
  - geographic focus (GCC, wider MENA, Africa, Europe, Asia, global)  
  - project_location_profile (conceptual patterns such as global_south, emerging_markets, offshore_islands, coastal_regions)  
  - immersive_modalities_focus (fulldome, planetariums, LBE/theme parks, media facades/LED domes, XR platforms, training and simulation)  
  - public–private partnership profile  
  - links to projects, institutions, policies and people  
  - sources and notes

- `institutions`  
  Ministries, development agencies, holding companies and other entities linked to immersive investment.

- `projects`  
  Immersive-relevant projects and infrastructures (domes, XR parks, media districts, destination experiences) funded or enabled by these investors, including:

  - project type and basic description  
  - country and city/region  
  - immersive formats in use (fulldome, XR, media facades, etc.)  
  - links to lead and co-investors, and operator institutions  
  - explicit `global_south_flag` and `offshore_flag` to mark Global-South and island/offshore contexts  
  - sources and temporal validity information

- `policies`  
  Vision programs, cultural strategies, national plans and frameworks (for example Saudi Vision 2030, Abu Dhabi’s tourism strategies) that explicitly or implicitly support immersive infrastructures.

- `people`  
  Key individuals connected to immersive investments (heads of entities, heads of entertainment, chiefs of tourism/experience portfolios, cultural leaders).

- `meta_instructions_for_ai`  
  Guidance for LLMs and agents on how to interpret, extend and query the dataset without hallucinating investors, projects or relationships.

- `data_contract`  
  A compact description of allowed transformations, expected update behaviour and validation rules.

---

## Pilot focus: Arab region

The initial version concentrates on:

- Saudi Arabia (Public Investment Fund, giga-projects, tourism and culture entities)  
- United Arab Emirates (Abu Dhabi and Dubai sovereign and strategic funds, tourism and entertainment developers)  

Within this region, special emphasis is placed on:

- funds and entities involved in giga-projects  
- destination developers (for example island and coastal destinations)  
- immersive exhibition projects, domes and experience centres  
- early-stage immersive platforms with regional roots

---

## Key results

The pilot reveals:

- a dense concentration of immersive-relevant capital in a small number of sovereign funds and strategic developers  
- strong integration of immersive content into tourism and soft-power strategies  
- a growing interest in immersive exhibitions, domes and XR venues as part of destination development  
- early signs of Global-South and island/offshore destinations becoming testbeds for new immersive formats

These findings are incomplete and will be extended as more investors and projects are added.

---

## Methodology (outline)

A more detailed methodology will be documented in `meta/methodology.md`. In outline:

1. Identification of relevant investors, institutions and programmes  
2. Collection of public documentation:
   - annual reports, strategy papers, official websites  
   - project descriptions, masterplans, giga-project concepts  
   - cultural and tourism programme documents  

3. Extraction of immersive-relevant information:
   - explicit immersive projects and venues  
   - entertainment and experience clusters  
   - media and culture components of wider development schemes  

4. Normalisation into the shared schema:
   - investor objects  
   - institution, project, policy and person entities  
   - cross-links via IDs  

5. Iterative updates:
   - new investors and projects added  
   - corrections and refinements as more sources become available  

All entries must be source-based; speculative numbers or invented entities are not allowed.

---

## Planned extensions

- expansion beyond the Arab region to:
  - Europe and the UK  
  - North America  
  - East and Southeast Asia  
  - Africa and Latin America  

- better quantification of immersive portfolio shares (where data is available)  
- deeper linkage to destination datasets (Immersive Destinations)  
- mapping skills and creative roles to investor-backed projects  
- thematic subsets for specific use cases (for example educational, museum and science communication projects)
- dedicated views for offshore and Global-South island projects, using the new Global-South and offshore flags

---

## Citation

If you refer to this dataset, please credit:

- Immersive Investors – curated by Martin Sambauer (martin-sambauer.com)

Example citation (text):

> The analysis is based on the Immersive Investors dataset (curated by Martin Sambauer), version X.Y.Z.

---

## Contact

For questions, collaboration or commercial projects, contact:

- Martin Sambauer  
- website: martin-sambauer.com  

---

## Temporal validity and review

The dataset is a snapshot and must be read with its timestamp:

- `dataset_metadata.snapshot_date`  
- `dataset_metadata.last_reviewed`

Entries may lag behind real-world changes. Users should:

- pay attention to the `data_valid_as_of` and `last_checked` fields on entities  
- consult primary sources for time-critical decisions

---

## Provenance and sources

The repository only contains entries with documented sources. Where possible:

- URLs and document titles are provided  
- multiple sources are used for triangulation  
- ambiguous or conflicting information is described in notes rather than silently resolved

This documentation is itself evolving and will be updated as the schema and dataset grow.
