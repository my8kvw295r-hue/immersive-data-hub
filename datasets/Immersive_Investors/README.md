## Immersive Investors – global capital for immersive infrastructures and experiences

Immersive Investors is a curated data repository mapping investors, funds, institutions and policies that support immersive infrastructures and experiences worldwide.

The repository is global in scope, but the pilot phase starts with a focus on the Arab region (GCC/MENA), where sovereign funds, tourism development programs and cultural initiatives play a leading role in immersive destination projects.

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

A dialectical view of immersive economics is central: immersive projects sit between culture and capital, between nation branding and local experience, between spectacle and structural transformation. Hyper-staged immersive constructs can act as accelerators of meaning, crystallising contradictions (tradition vs futurism, nature vs megastructure, authenticity vs staging) into visible, discussable forms.

This conceptual layer is what makes the data usable for analysis, journalism, LLMs and agents rather than just a list of names.

---

## Repository structure

Suggested structure for this repository:

- `datasets/`  
  Main JSON files with structured information.

  - `datasets/immersive_investors_global_v01.json`  
    Global file with investors, institutions, projects, policies and people.  
    The pilot version starts with Arab region entries; later versions add other regions.

  - `datasets/subsets/`  
    Optional regional or thematic slices derived from the global file, e.g.:
    - `arab_region.json`
    - `gcc_immersive_investors.json`
    - `festivals_and_cultural_foundations.json`

- `meta/`  
  Methodology notes, data contracts, AI instructions.

  - `meta/methodology.md`  
  - `meta/schema.json`  
  - `meta/data_contract.json`  
  - `meta/meta_instructions_for_ai.json`

- `docs/`  
  Additional documentation excerpts, diagrams or article snippets.

Each dataset in this repository should:

- follow the global investor schema  
- document sources and limitations  
- be compatible with cross-linking to other immersive datasets (destinations, skills, directors)

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
    - preferred stages (seed, growth, infrastructure, late-stage content, venue development)  
    - typical ticket size ranges  
  - instruments (equity, project finance, PPP, grants, mixed)  
  - thematic focus (tourism, culture, sports, smart city, metaverse, museums, creative industries)  
  - geographic focus (GCC, wider MENA, Africa, Europe, Asia, global)  
  - public–private partnership profile  
  - links to projects, institutions, policies and people  
  - sources and notes

- `institutions`  
  Ministries, development agencies, holding companies and other entities linked to immersive investment.

- `projects`  
  Immersive-relevant projects and infrastructures (domes, XR parks, media districts, destination experiences) funded or enabled by these investors.

- `policies`  
  Vision programs, cultural strategies, national plans and frameworks (for example 2030 visions, tourism pillars) that explicitly or implicitly support immersive infrastructures.

- `people`  
  Key individuals connected to immersive investments (heads of entertainment, chiefs of tourism/experience portfolios, cultural leaders).

- `meta_instructions_for_ai`  
  Guidance for LLMs and agents on how to interpret, extend and query the dataset without hallucinating investors, projects or numbers.

- `data_contract`  
  Structural expectations and constraints for validators and tools (required fields, value ranges, ID patterns).

---

## Pilot focus: Arab region

The first versions of `immersive_investors_global_v01.json` will primarily contain:

- GCC and wider MENA sovereign wealth funds with immersive-relevant activity  
- tourism and entertainment development funds  
- large-scale destination projects with strong immersive components  
- policies and vision programmes (for example tourism, culture, entertainment and giga-projects)  
- key people responsible for entertainment, tourism and experiential portfolios

Over time, these entries will be complemented by investors and projects from other regions, using the same schema.

---

## Key results

Key results depend on the current content of the dataset and are not stored statically in this README.

Typical dynamic insights that can be generated from the dataset include:

- distribution of investor types by region and immersive focus  
- temporal maturity of immersive portfolios in the Arab region vs other regions  
- patterns of PPP structures across tourism and entertainment projects  
- correlations between national vision programmes and immersive infrastructures  
- how much of an investor’s visible portfolio is structurally immersive (venues, experiential districts, XR parks, media architecture)

For up-to-date quantitative and structural results, load the JSON file into an analysis notebook or an LLM and request summaries or comparisons.

A conceptual layer of stable interpretative insights will be added to this README once the first pilot entries are populated and analysed.

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

---

## Citation

If you use this repository or its datasets, please cite:

Immersive Investors, curated by Martin Sambauer (martin-sambauer.com).  
Global dataset on investors, institutions and policies for immersive infrastructures and experiences.  
Licensed under CC BY 4.0.

---

## Contact

For questions, corrections or collaboration related to immersive investors and immersive economics:

Website: https://martin-sambauer.com  
Contact details are listed on the website.

---

## Temporal validity and review

Each dataset version is treated as a dated snapshot.

- `dataset_metadata.snapshot_date` records the ISO date (YYYY-MM-DD) of the snapshot for this JSON file.
- `dataset_metadata.last_reviewed` records the ISO date when the dataset as a whole was last curator-reviewed.
- Each entity (`investors`, `institutions`, `projects`, `policies`, `people`) has:
  - `data_valid_as_of` – the date the information is considered valid as of.
  - `last_checked` – the date when a human curator or trusted agent last reviewed the entry.

Analyses should always treat these dates as lower bounds: if `last_checked` is older than 12–18 months, downstream tools should consider the entry potentially outdated and prioritise it for refresh.

---

## Provenance and sources

Every factual value in the dataset must be traceable to at least one external source:

- Entities must list one or more `sources` objects with URLs or formal references.
- Curators must only enter values that are explicitly supported by at least one listed source.
- If no supporting source exists, the field must be set to `null` rather than guessed.

The current schema keeps provenance at entity level (via the `sources` array). For future, more granular temporal or field-level provenance, additional per-field `source_ids` can be added, but this is out of scope for the pilot.

