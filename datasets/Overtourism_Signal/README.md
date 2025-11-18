## Global Overtourism Discourse and Stakeholder Dataset (n+1)

This repository folder contains the n+1 qualitative layer on overtourism for selected destinations. It is designed as a discourse and stakeholder dataset that sits on top of the quantitative core dataset Immersive_Destination_Analysis.

The purpose of this n+1 dataset is to capture who is speaking about overtourism, what they are saying, how they frame problems and solutions, and how strong local awareness and conflict levels are. It is built for concept validation, service design and partnership development around immersive communication and destination stewardship.

## Relationship to the core dataset (n)

Core dataset (n)

- Name: Immersive_Destination_Analysis
- Repository folder: https://github.com/martin-sambauer/immersive-datasets/tree/main/datasets/Immersive_Destination_Analysis
- Data file (GitHub view): https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/Immersive_Destination_Analysis.json
- Raw JSON: https://raw.githubusercontent.com/martin-sambauer/immersive-datasets/main/datasets/Immersive_Destination_Analysis/Immersive_Destination_Analysis.json
- README: https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/README.md
- Methodology: https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/methodology.md
- Schema: https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/schema.json
- Raw schema: https://raw.githubusercontent.com/martin-sambauer/immersive-datasets/main/datasets/Immersive_Destination_Analysis/schema.json

The Immersive_Destination_Analysis dataset is the neutral, quantitative baseline. It focuses on tourism throughput, investment conditions, sustainability, real estate structures and immersive storytelling potential.

The overtourism n+1 dataset never replaces the core dataset. It only adds a qualitative discourse layer that can refer back to destinations in the core dataset when relevant.

## Scope of the overtourism n+1 dataset

The n+1 dataset concentrates on destinations where overtourism is a visible issue in public discourse. It explicitly aims to over-sample locations with strong:

- crowding and carrying capacity problems
- environmental and heritage stress
- conflicts between residents, tourism stakeholders and authorities
- calls for regulation, redistribution of visitor flows or new communication strategies

The dataset includes two types of destinations:

1. Linked core destinations  
   Destinations that already exist in Immersive_Destination_Analysis and are referenced by their destination_id.

2. External enrichment destinations  
   Destinations that show strong overtourism discourse but are not yet represented in the core dataset. These can later be promoted to the core dataset if full structural data is researched.

This means the n+1 dataset can contain more destinations than the n dataset. It is not designed to be representative of global tourism as a whole. It is a focused layer on overtourism discourse.

## Target groups and use cases

The overtourism discourse dataset is intended for:

- destination managers and sustainability officers
- public authorities and destination marketing organisations
- immersive media producers and creative directors
- investors and impact funds interested in destination stewardship
- researchers and journalists working on overtourism

Typical use cases:

- identifying destinations with high overtourism awareness and conflict levels
- mapping critical voices and stakeholder types (government, NGOs, residents, business, research)
- understanding how problems and proposed solutions are framed
- validating concepts for immersive communication and visitor education
- building outreach and partnership lists for interviews, service offers and PPP initiatives

## Data structure overview

The n+1 dataset is stored as a single JSON file with the following top-level structure:

- dataset_meta  
  Metadata for the dataset, including a reference to the core dataset.

- cases  
  Overtourism cases per destination. Each case describes the overtourism situation, issues and awareness level for one place.

- actors  
  Stakeholders who appear in the discourse, such as local officials, NGOs, researchers, resident groups or tourism businesses.

- statements  
  Individual statements about overtourism, linked to both a case and an actor.

### Cases

A case object captures the overtourism situation for a destination:

- case_id  
- destination_ref (name, optional destination_id, provenance, in_main_dataset flag)  
- research_window (from_year, to_year)  
- issues (tags and comment)  
- awareness_assessment (awareness level, conflict intensity, policy response, assessment basis, notes)  
- statement_ids (ids of linked statements)  
- meta (last_researched_utc, researcher_notes, sources_overview)

### Actors

An actor object represents a person or collective actor who appears in the overtourism discourse:

- actor_id  
- name  
- actor_type (such as local_government, ngo, resident, academic_researcher, tourism_business_owner)  
- role_title and organisation  
- sector (public, private, civil_society, research)  
- location  
- is_collective_actor  
- contact_relevance (for_interviews, for_partnerships, comment)

### Statements

A statement object represents a single quote or paraphrased statement about overtourism:

- statement_id  
- case_id and actor_id  
- source (source_id, type, title, url, publisher, publication_date, language, accessed_at_utc)  
- original_quote (if legally and ethically permissible)  
- paraphrase_en and paraphrase_de  
- content_coding (primary_issues, secondary_issues, problem_framing, attributed_causes, proposed_solutions)  
- tone_and_stance (stance_towards_tourism, tone, calls_for_action)  
- relevance_for_immersive_interventions (mentions_storytelling_or_communication, potential_intervention_themes, notes)

The JSON schema in schema.json defines this structure precisely and is the authoritative reference for validation.

## Data quality and integrity rules

This dataset follows strict integrity principles:

- No invented or fabricated sources  
  Every source in the dataset must correspond to a real, verifiable document, article, report, interview or public statement. If a URL is stored, it must resolve to a real resource at the time of research.

- No fabricated quotes or paraphrases  
  Original quotes must only be included if they are actually present in the source. Paraphrases must be faithful to the original content and must not add meaning that is not supported by the source.

- No hallucinated actors or roles  
  Every actor must be a real person or organisation that can be verified from the cited sources.

- Explicit handling of uncertainty  
  Where assessments (such as awareness_level or conflict_intensity) are interpretative, this must be flagged via an assessment_basis field and, where relevant, notes that explain the reasoning.

- Clear separation between fact and interpretation  
  Factual fields must be based directly on sources. Aggregated assessments and coding (for example problem_framing or potential_intervention_themes) must be clearly marked as interpretative coding.

If information cannot be supported by a real source, it must not be added to the dataset. Fields should be left null instead of guessing or inventing content.

## Use by tools and AI systems

This dataset is explicitly designed to be machine friendly.

Tools and AI systems using this dataset must follow these rules:

- Always load the JSON file and iterate over the arrays cases, actors and statements.  
- Never reconstruct lists of cases or actors manually from rendered snippets or screenshots.  
- Treat the JSON schema as the single source of truth for field names and data types.  
- Never fabricate statements, actors, sources or content that are not present in the dataset or in real external sources.  
- When suggesting extensions, always mark them as proposals that need human research and verification before being added to the dataset.  
- If a requested field or case does not exist, return null or an explicit explanation instead of inventing data.

These rules are binding for manual editing, scripted imports and AI assisted work.

## File structure

The n+1 overtourism dataset uses the following files:

- Overtourism_Discourse_Nplus1.json  
  Main dataset file with dataset_meta, cases, actors and statements.

- README.md  
  Overview and usage notes for the dataset.

- methodology.md  
  Detailed explanation of scope, research methods, coding scheme and validation rules.

- schema.json  
  JSON Schema that all dataset files must validate against.

The dataset will be published in the same GitHub repository as the core dataset, under a dedicated subfolder in datasets.

## Versioning

Dataset ID

- MARTIN_SAMBAUER_OVERTOURISM_NPLUS1_V1

Versioning principles:

- New cases, actors and statements are added in an append-only fashion.  
- IDs (case_id, actor_id, statement_id, source_id) are never recycled.  
- Breaking changes to the schema result in a new major dataset version (for example V2).  
- Each release is documented in dataset_meta.version_notes and in the changelog section of methodology.md.

## Contact

Author and curator  
Martin Sambauer  
https://martin-sambauer.com

## Explore and licensing

Explore. repository folder · JSON · article with insights  
Licensing. CC BY 4.0 · © Martin Sambauer · martin-sambauer.com
