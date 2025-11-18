## Methodology for the Global Overtourism Discourse and Stakeholder Dataset (n+1)

This document describes the scope, concepts, research procedures and validation rules for the overtourism n+1 dataset. It is intended for researchers, tools and AI systems that work with or extend this dataset.

## 1. Scope and goals

The overtourism n+1 dataset is a qualitative discourse and stakeholder layer that focuses on overtourism in selected destinations. It does not aim to be a globally representative sample. Instead, it concentrates on locations where overtourism is visible in public discourse and where there is potential for immersive communication and destination stewardship interventions.

Goals:

- document critical voices and narratives about overtourism
- identify who speaks about problems and solutions (actors and roles)
- capture how issues are framed and which solutions are proposed
- provide a basis for concept validation and service design around immersive communication, visitor education and public private partnerships

## 2. Relationship to the core dataset (n) and enrichment logic

The n+1 dataset is conceptually and technically separated from the core dataset Immersive_Destination_Analysis.

2.1 Core dataset (n)

The core dataset is the neutral baseline. It captures:

- destination identity and classification
- tourism throughput and visitor profiles
- economic indicators and investment climate
- real estate structures and pricing
- sustainability profile and overtourism signals
- attraction metadata and immersive storytelling potential

It is designed to be as balanced and neutral as possible within its Global South focus and selected benchmark locations.

2.2 Overtourism dataset (n+1)

The n+1 dataset focuses on:

- destinations where overtourism is problematised in public discourse
- critical voices from different stakeholder groups
- local awareness and conflict levels
- problem framings and proposed solutions

Selection is intentionally biased towards overtourism. The dataset is not a representative sample of all destinations. It is a problem focused layer.

2.3 Enrichment from two sources

Destinations in the n+1 dataset come from two sources:

- linked core destinations  
  Destinations that already exist in Immersive_Destination_Analysis. They are referenced by destination_id via the destination_ref field.

- external enrichment destinations  
  Destinations identified through qualitative research on overtourism discourse, even if they are not yet represented in the core dataset.

For external enrichment destinations, destination_ref.destination_id is null and in_main_dataset is set to false. An optional flag candidate_for_main_dataset can signal that a destination should be considered for future inclusion in the core dataset once structural data has been collected.

This separation ensures that the core dataset stays neutral and that the n+1 dataset can deliberately focus on overtourism hot spots.

## 3. Data model

The overtourism dataset uses three main collections in a single JSON file:

- cases  
- actors  
- statements  

The JSON schema in schema.json defines the exact structure.

3.1 Cases

Each case represents the overtourism situation in a specific destination.

Typical fields:

- case_id  
  Unique identifier, for example OTC_01, OTC_02, with sequential numbering that is never reused.

- destination_ref  
  Object that links the case to a destination, including:
  - destination_id (string or null)
  - destination_name (string)
  - in_main_dataset (boolean)
  - provenance (for example from_main_dataset or external_enrichment)
  - candidate_for_main_dataset (optional boolean)

- research_window  
  from_year and to_year that describe the time frame considered for this case.

- issues  
  Controlled tags describing observed issues, such as crowding, heritage_damage, housing_pressure, cruise_tourism, water_stress, waste_management, traffic_congestion. A free text comment field documents the logic.

- awareness_assessment  
  Assessment of awareness and conflict levels, including:
  - awareness_level (low, medium, high)
  - conflict_intensity (low, medium, high)
  - policy_response_level (low, medium, high)
  - assessment_basis (for example interpretative or mixed)
  - notes (short explanation of the assessment)

- statement_ids  
  List of statement_id values that belong to this case.

- meta  
  Meta information such as last_researched_utc, researcher_notes and sources_overview. Sources_overview is a short list of key sources used for this case, with fields id, title, url and source_type.

3.2 Actors

Actors represent people or collective entities who appear in the overtourism discourse.

Typical fields:

- actor_id  
  Unique identifier, such as ACT_0001.

- name  
  The personal or organisational name.

- actor_type  
  A controlled category such as local_government, regional_government, national_government, destination_marketing_organisation, tourism_board, ngo, community_group, resident, academic_researcher, tourism_business_owner, hospitality_operator, cruise_operator, investor, activist_group, visitor.

- role_title and organisation  
  Optional role title and organisation name.

- sector  
  For example public, private, civil_society, research.

- location  
  Free text description of the main location, usually city and country.

- is_collective_actor  
  Boolean flag that indicates whether this is a collective actor (for example a resident association) or an individual.

- contact_relevance  
  Object describing:
  - for_interviews (boolean)
  - for_partnerships (boolean)
  - comment (optional text)

3.3 Statements

Statements represent individual contributions to the overtourism discourse.

Typical fields:

- statement_id  
  Unique identifier, such as STM_0001.

- case_id and actor_id  
  References to the case and the actor this statement belongs to.

- source  
  Object that documents the origin of the statement:
  - source_id
  - source_type (local_media, national_media, academic_paper, ngo_report, government_document, social_media, press_release, other)
  - title
  - url
  - publisher
  - publication_date
  - language
  - accessed_at_utc

- original_quote  
  Original quote text if legally and ethically permissible. If quoting is not appropriate, this field is set to null.

- paraphrase_en and paraphrase_de  
  Carefully written paraphrases in English and German that preserve the meaning of the original statement without adding unsupported claims.

- content_coding  
  Object describing the thematic coding:
  - primary_issues (list of tags)
  - secondary_issues (list of tags)
  - problem_framing (for example individual, systemic, governance, market, environmental)
  - attributed_causes (list of short strings)
  - proposed_solutions (list of short strings)

- tone_and_stance  
  Object describing:
  - stance_towards_tourism (supportive, balanced, critical, anti_tourism)
  - tone (neutral, concerned, urgent, outraged, optimistic)
  - calls_for_action (boolean)

- relevance_for_immersive_interventions  
  Object that links the discourse to possible immersive interventions:
  - mentions_storytelling_or_communication (boolean)
  - potential_intervention_themes (list of themes, for example visitor_education, redistribution_of_flows, carrying_capacity_explanation, cultural_sensitivity, climate_impacts)
  - notes (short free text)

## 4. Research workflow and source collection

4.1 Identification of destinations and cases

Destinations and overtourism cases are identified through:

- local and national media coverage
- academic articles and reports
- NGO and civil society publications
- government and planning documents
- statements by destination marketing organisations and tourism boards
- carefully selected social media discussions when they are clearly attributable to identifiable actors

The selection intentionally focuses on destinations where overtourism is not only present as a phenomenon but is also explicitly discussed in public discourse.

4.2 Source collection and documentation

For each case and statement, sources are collected and documented as follows:

- Every source must be a real, verifiable document or resource.  
- At least one clear citation or URL must be kept for each case.  
- For statements, source information is stored in the source object inside the statement and optionally aggregated in meta.sources_overview at case level.

If a source is behind a paywall or in print only, a descriptive title and reference must be stored so that it can be located again through libraries or databases.

4.3 Explicit rule against fabricated sources and content

There is a strict rule:

- No source, actor, quote, paraphrase or statement may be fabricated or hallucinated.  
- If a statement or actor cannot be linked to a real, verifiable source, it must not be entered into the dataset.  
- If a piece of information cannot be reliably reconstructed, the corresponding field must be left null.

This rule applies equally to manual work and to any AI assisted workflow.

## 5. Coding scheme

5.1 Issues tags

Issues tags are used consistently across cases and statements. Typical tags include:

- crowding
- heritage_damage
- housing_pressure
- cruise_tourism
- water_stress
- waste_management
- traffic_congestion
- noise
- price_pressure
- safety_and_security
- climate_impact

Tags may be extended in a controlled way. New tags should be documented in a separate coding reference document if the list grows.

5.2 Awareness and conflict assessment

Awareness and conflict levels are assessed at case level:

- awareness_level  
  low, medium or high

- conflict_intensity  
  low, medium or high

- policy_response_level  
  low, medium or high, describing whether authorities have responded with regulations, plans or concrete measures

These assessments are interpretative summaries based on the available sources. The assessment_basis field must always indicate that they are interpretative. Where necessary, notes provide a short justification, for example number and tone of media articles and presence of protests or political debates.

5.3 Problem framing and solutions

At statement level, problem_framing and proposed_solutions are used to capture how actors think about overtourism.

Examples for problem_framing:

- individual (behaviour of tourists)
- systemic (governance, markets, global tourism model)
- governance (local or national regulation)
- market (prices, investment flows)
- environmental (carrying capacity, emissions, biodiversity)

Proposed solutions include concrete measures such as:

- visitor caps
- changes in tourist tax
- regulation of short term rentals
- redistribution of visitor flows
- investment in public transport
- immersive visitor education and interpretation

These fields are coded based on the content of the statement and must not introduce ideas that are not supported in the source.

## 6. Validation and integrity checks

6.1 Schema validation

Before release, the dataset must validate against schema.json. This ensures:

- correct data types
- required fields are present
- no unknown top-level properties are introduced

6.2 ID uniqueness

The following IDs must be unique within the dataset:

- case_id  
- actor_id  
- statement_id  
- source_id

IDs are never recycled. If an element is removed, its ID is not used again.

6.3 Consistency checks

Additional checks include:

- every case referenced in statements exists in cases  
- every actor referenced in statements exists in actors  
- every statement in statement_ids of a case actually exists and points back to that case  
- destination_ref.in_main_dataset is consistent with the presence or absence of destination_id

6.4 No fabricated content rule for AI and automation

All automated or AI assisted processes must:

- treat the dataset and schema as constraints, not suggestions  
- never invent sources, actors or quotes that do not exist in real external material  
- always request human review and verification before adding new content derived from external sources  
- clearly flag any incomplete or missing information as null or unknown instead of filling gaps with guesswork

Violating this rule breaks the integrity of the dataset and is not permitted.

## 7. Limitations and bias

The dataset has several built in limitations:

- It is intentionally biased towards destinations with visible overtourism discourse.  
- It does not aim to measure global prevalence of overtourism.  
- It is limited by language coverage and the availability of sources.  
- Social media and informal sources are only included when attribution and reliability can be established.

Users should not treat this dataset as a statistical sample. It is best used for:

- qualitative case comparisons  
- identification of patterns in discourse and governance  
- design of interventions and services  
- exploration of possible public private partnership opportunities

## 8. Versioning and future extensions

Dataset ID

- MARTIN_SAMBAUER_OVERTOURISM_NPLUS1_V1

Future versions may add:

- more destinations and cases  
- a richer actor typology  
- more detailed coding for solutions and governance instruments  
- separate source collections for complex cases

Major changes to the schema will result in a new version suffix and will be documented both in dataset_meta.version_notes and here in the methodology.

## 9. Attribution

Please use the following attribution in publications:

Sambauer, Martin (2025)  
Global Overtourism Discourse and Stakeholder Dataset (MARTIN_SAMBAUER_OVERTOURISM_NPLUS1_V1), CC BY 4.0.  
https://martin-sambauer.com

## Explore and licensing

Explore. repository folder · JSON · article with insights  
Licensing. CC BY 4.0 · © Martin Sambauer · martin-sambauer.com
