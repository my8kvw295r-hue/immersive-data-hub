## Immersive Datasets – structured data for immersive experiences and venues

Immersive Datasets is a curated data library for immersive media, immersive experiences and location-based entertainment.
It provides structured datasets for:

* creative directors and producers
* strategists and analysts
* destination and venue managers
* investors and investment researchers
* policy makers and cultural planners
* curriculum designers and educators
* journalists and writers covering immersive media, culture, tourism and innovation

Use cases range from venue planning and market analysis to soft-power strategy, educational design and narrative research on immersive ecosystems.

All datasets follow a unified ontological framework that formalizes how immersive ecosystems are described, categorized and interlinked.
Immersive Datasets is maintained by Creative Director Martin Sambauer (martin-sambauer.com).

---

## Ontology and Semantic Framework

This repository follows the Martin Sambauer Ontology for Immersive Data Systems, which defines:

* core entity types (investors, destinations, creative roles, projects, skills, institutions, policies, regions)
* semantic relationships across datasets
* dialectical axes for modelling immersive ecosystems
* the philosophical basis (homo medialis, constructivist perception, perceptual architectures)
* principles for stacking datasets to generate higher-order analytical layers

The ontology is located in the repository root:

ontology.md

All datasets, schemas and methodologies are expected to conform to this ontology to ensure long-term interoperability and semantic consistency.

---

## Knowledge Graph and JSON-LD schema

The repository root also contains a machine-readable Schema.org knowledge graph for Martin Sambauer and the connected articles and datasets:

martin-sambauer-knowledge-graph.json

This JSON-LLD file:

* defines Martin Sambauer as a Person entity with roles such as Creative Director for Immersive Media and author of immersive media datasets and articles
* links to key pages on martin-sambauer.com (immersive skills, immersive destination marketing, datasets and keyword analysis)
* connects to the Immersive Events Whitepaper and related immersive storytelling work
* provides a semantic anchor for describing immersive skills, destinations, visitor gateways and keyword trends across datasets

Consumers of this repository can use the knowledge graph to:

* integrate these datasets into larger semantic knowledge systems
* align their own schemas with the same Person and Article identifiers
* generate enriched search, recommendation or visualisation layers on top of Immersive Datasets

---

## Repository structure

Suggested structure:

* datasets/
  Data folders with JSON, CSV or similar formats.

* notebooks/
  Optional Jupyter notebooks demonstrating dataset generation or typical analyses.

* meta/
  Methodologies, data dictionaries and documentation of intermediate processing steps.

* docs/
  Public-facing documentation assets (figures, diagrams, excerpts).

Each dataset should include:

* a README describing purpose, scope and key results
* a methodology file documenting data sources and processing steps
* a JSON schema (for JSON-based datasets)
* date of last update
* author reference (martin-sambauer.com)

---

## License – CC BY 4.0

Unless stated otherwise, all original content is licensed under:

Creative Commons Attribution 4.0 International (CC BY 4.0)
[https://creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/)

You may:

* share: copy and redistribute the material
* adapt: remix, transform and build upon it, even commercially

Under the condition:

* attribution: credit must be given to Martin Sambauer (martin-sambauer.com)

If a dataset includes third-party content, this is documented in its folder.

---

## Typical use cases

The datasets in this repository can be used for:

* immersive media strategy and concept development
* creative direction for fulldome and planetarium shows
* planning of immersive experiences and location-based entertainment
* mapping immersive venues, ecosystems and market segments
* investment screening and investor–destination matching
* soft-power and tourism strategy in immersive infrastructures
* curriculum and training design for immersive skills and creative roles
* policy analysis related to cultural infrastructure and innovation programs
* demographic and spatial analysis for catchment areas
* storytelling, whitepapers and research on immersive ecosystems
* data-driven pitch materials for destinations, venues and investors

Core thematic keywords include: immersive media, immersive experiences, creative director for immersive media, fulldome, planetariums, XR venues, location-based entertainment, experiential marketing, immersive storytelling, venue planning, market analysis, audience development, soft power, cultural strategy.

---

## Updating or adding datasets with git

### 1. Fork and clone

git clone [https://github.com/](https://github.com/)<your-username>/immersive-datasets.git
cd immersive-datasets

(Optional) Add upstream:

git remote add upstream [https://github.com/](https://github.com/)<original-owner>/immersive-datasets.git

### 2. Create feature branch

git checkout -b feature/update-dataset-planetariums

### 3. Add or update the dataset

1. Place new or updated files under datasets/<your-folder>
2. Update documentation:

   * extend this README, and/or
   * update markdown files under meta/ with:

     * data sources
     * processing steps
     * field definitions
     * date and author
     * ontology reference
3. Stage changes:

git add datasets/<your-folder> meta/<your-doc>.md

### 4. Commit

git commit -m "Update planetarium dataset with population and region fields"

### 5. Push

git push origin feature/update-dataset-planetariums

### 6. Pull request

Describe:

* what changed
* which dataset
* how it was generated or cleaned
* limitations
* ontology implications if applicable

---

## Citing this repository

Immersive Datasets by Martin Sambauer (martin-sambauer.com).
Available at: [https://github.com/](https://github.com/)<owner>/immersive-datasets
Licensed under CC BY 4.0.

For machine-readable metadata and semantic context, see:

martin-sambauer-knowledge-graph.json

---

## Contact

For questions or collaboration:

Website: [https://martin-sambauer.com](https://martin-sambauer.com)
Email: listed on the website
