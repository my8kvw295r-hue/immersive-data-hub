# Overtourism n+1 Dataset – Full Methodology (Comprehensive Version)

This document defines the complete methodological, conceptual, and structural foundations of the **Overtourism n+1 Dataset**. It is designed for researchers, data engineers, analysts, and AI systems working with global overtourism discourse. This version merges the clarity of a layered architecture (n vs. n+1) with a detailed, field-level description.

---

## 0. Relationship Between n and n+1

The n+1 dataset is an analytical extension of the parent dataset **Immersive_Destination_Analysis (n)**.

### n dataset (baseline)

The core dataset provides neutral structural data:

* destination identity and classification
* geographic and demographic context
* tourism throughput and visitor composition
* economic indicators
* sustainability profiles and indicators
* immersive storytelling and infrastructure metadata

### n+1 dataset (discourse and stakeholder layer)

The n+1 dataset adds a qualitative overtourism discourse layer, capturing:

* stakeholder voices and roles
* overtourism narratives and conflicts
* awareness levels and problem framings
* proposed solutions and governance responses
* NGO activity and pressure
* institutional responsibilities
* media coverage intensity
* economic dependency on tourism

### Enrichment logic

Destinations in n+1 come from two sources:

1. **Core-linked destinations** (already present in Immersive_Destination_Analysis)
   These are referenced by `destination_ref.destination_id` and marked with `in_main_dataset = true`.

2. **External enrichment destinations** (discovered through discourse research)
   These may not yet exist in the n dataset and are stored with:

   * `destination_id = null`
   * `in_main_dataset = false`
   * optional `candidate_for_main_dataset = true`

This separation keeps the n dataset neutral and balanced while allowing n+1 to focus deliberately on overtourism hotspots and conflict constellations.

---

## 1. Scope and Goals

The overtourism n+1 dataset is a **qualitative discourse and stakeholder layer**. It does not claim global representativeness. Instead, it concentrates on destinations where:

* overtourism is visible in public discourse
* conflicts and tensions are documented
* potential for immersive communication and destination stewardship exists

Goals:

* document critical voices and narratives about overtourism
* identify who speaks about problems and solutions (actors and roles)
* capture how issues are framed and which solutions are proposed
* analyse NGO activity and institutional landscapes
* measure and classify media pressure and NGO pressure
* approximate tourism dependency (via GDP-related indicators)
* provide a basis for concept validation and service design around immersive communication, visitor education and public–private partnerships

---

## 2. Data Model Overview

The dataset uses three main collections inside a single JSON file:

* **cases** – destination-level discourse objects
* **actors** – people and collective entities
* **statements** – individual contributions to the discourse

The JSON schema in `schema.json` defines the precise structure. All examples below are conceptual; the schema is the formal reference.

---

## 3. Cases

Each Case represents the overtourism situation in a specific destination over a defined period.

### 3.1 Core fields

* **case_id**
  Unique identifier, for example `OTC_001`, `OTC_002`. Sequential numbering is recommended and IDs are never reused.

* **destination_ref**
  Object linking the Case to a destination:

  * `destination_id` (string or null)
  * `destination_name` (string)
  * `in_main_dataset` (boolean)
  * `provenance` (e.g. `from_main_dataset`, `external_enrichment`)
  * `candidate_for_main_dataset` (optional boolean)

* **research_window**
  Object describing the time frame considered for this Case:

  * `from_year`
  * `to_year`

* **issues**
  Object containing:

  * `tags` (list of controlled issue tags)
  * `comment` (short description of why these tags were chosen)

* **awareness_assessment**
  Object capturing awareness and conflict levels:

  * `awareness_level` (low, medium, high)
  * `conflict_intensity` (low, medium, high)
  * `policy_response_level` (low, medium, high)
  * `assessment_basis` (e.g. `interpretative`, `mixed`)
  * `notes` (short justification)

* **media_pressure_level**
  Controlled taxonomy value (see Section 6.1).

* **ngo_pressure_level**
  Controlled taxonomy value (see Section 6.2).

* **tourism_dependency_level**
  Controlled taxonomy value (see Section 6.3).

* **statement_ids**
  List of `statement_id` values belonging to this Case.

* **meta**
  Object containing:

  * `last_researched_utc` (timestamp)
  * `researcher_notes` (free text)
  * `sources_overview` (list of key sources with `id`, `title`, `url`, `source_type`)

### 3.2 NGO and institutional fields at Case level

In addition to issues and awareness, a Case may include aggregated NGO and institutional indicators:

* `ngos_involved_count`
  Integer count of documented NGOs.

* `media_pressure_level` and `ngo_pressure_level`
  Interpreted taxonomies based on evidence.

* `tourism_dependency_level`
  Categorisation of how dependent the destination’s economy is on tourism, based on available data.

All such assessments must be backed by traceable sources and include at least one timestamp indicating when the information was valid or retrieved.

---

## 4. Actors

Actors represent people or organisations involved in the overtourism discourse.

### 4.1 Core fields

* **actor_id**
  Unique identifier, such as `ACT_0001`.

* **name**
  Personal or organisational name.

* **actor_type**
  Controlled category, for example:

  * `local_government`
  * `regional_government`
  * `national_government`
  * `destination_marketing_organisation`
  * `tourism_board`
  * `ngo`
  * `community_group`
  * `resident`
  * `academic_researcher`
  * `tourism_business_owner`
  * `hospitality_operator`
  * `cruise_operator`
  * `investor`
  * `activist_group`
  * `visitor`

* **role_title** and **organisation**
  Optional but recommended, especially for institutional actors.

* **sector**
  For example `public`, `private`, `civil_society`, `research`.

* **location**
  Free text description (typically city and country).

* **is_collective_actor**
  Boolean flag indicating whether the actor is a collective entity (e.g. resident association) or an individual.

### 4.2 Institutional metadata

For institutional actors (destination managers, sustainability managers, tourism boards, authorities), additional fields may be captured:

* `supervising_ministry`
  Ministry the organisation reports to (if documented).

* `budget_information`
  Descriptive field for public budgets or funding structures when available.

* `institutional_timestamp_utc`
  Timestamp indicating when this information was retrieved or confirmed.

### 4.3 Contact relevance

* **contact_relevance** object:

  * `for_interviews` (boolean)
  * `for_partnerships` (boolean)
  * `comment` (text)

This enables the dataset to serve as a basis for outreach to key stakeholders.

---

## 5. Statements

Statements represent individual contributions to the overtourism discourse.

### 5.1 Core fields

* **statement_id**
  Unique identifier, e.g. `STM_0001`.

* **case_id** and **actor_id**
  References to the Case and Actor this statement belongs to.

* **source** object:

  * `source_id`
  * `source_type` (e.g. `local_media`, `national_media`, `academic_paper`, `ngo_report`, `government_document`, `social_media`, `press_release`, `other`)
  * `title`
  * `url`
  * `publisher`
  * `publication_date`
  * `language`
  * `accessed_at_utc`

* **original_quote**
  Original quote text, if legally and ethically permissible. If quoting is not appropriate, this field is set to null.

* **paraphrase (English only)**
  Carefully written paraphrase in English that preserves the meaning of the original statement without adding unsupported claims.

### 5.2 Content coding

* **content_coding** object:

  * `primary_issues` (list of tags)
  * `secondary_issues` (list of tags)
  * `problem_framing` (e.g. `individual`, `systemic`, `governance`, `market`, `environmental`)
  * `attributed_causes` (list of short strings)
  * `proposed_solutions` (list of short strings)

### 5.3 Tone and stance

* **tone_and_stance** object:

  * `stance_towards_tourism` (e.g. `supportive`, `balanced`, `critical`, `anti_tourism`)
  * `tone` (e.g. `neutral`, `concerned`, `urgent`, `outraged`, `optimistic`)
  * `calls_for_action` (boolean)

### 5.4 Relevance for immersive interventions

* **relevance_for_immersive_interventions** object:

  * `mentions_storytelling_or_communication` (boolean)
  * `potential_intervention_themes` (list of themes such as `visitor_education`, `redistribution_of_flows`, `carrying_capacity_explanation`, `cultural_sensitivity`, `climate_impacts`)
  * `notes` (short free text)

---

## 6. Taxonomies

### 6.1 Media Pressure Taxonomy

Media pressure at Case level is coded as:

* `None` — no visible overtourism discourse in media
* `Low` — few local articles or sporadic coverage
* `Mid` — regular local or national coverage
* `High` — strong, continuous coverage, overtourism is a visible conflict
* `Extreme` — international visibility, crisis or scandal framing

### 6.2 NGO Pressure Taxonomy

NGO pressure at Case level is coded as:

* `None` — no documented NGO involvement
* `Low` — isolated statements, small campaigns
* `Mid` — multiple NGOs, sustained attention
* `High` — organised campaigns, significant local influence
* `Extreme` — strong national or international NGO coalitions, high-pressure campaigns

### 6.3 Tourism Dependency Taxonomy

Tourism dependency is expressed as GDP share categories:

* `Low` (<5%)
* `Mid` (5–15%)
* `High` (15–30%)
* `Very High` (30–50%)
* `Extreme` (>50%)

Each taxonomic assignment must be supported by data or credible estimates from:

* official statistics
* academic work
* reputable economic reports

Every such datapoint should include a timestamp and a documented source.

---

## 7. Coding Scheme Detail

### 7.1 Issue tags

Issues tags are used consistently across Cases and Statements. Typical tags include:

* `crowding`
* `heritage_damage`
* `housing_pressure`
* `cruise_tourism`
* `water_stress`
* `waste_management`
* `traffic_congestion`
* `noise`
* `price_pressure`
* `safety_and_security`
* `climate_impact`
* `infrastructure_overload`
* `plastic_pollution`
* `ecosystem_stress`
* `biodiversity_loss`
* `social_conflict_protests`
* `ngo_pressure`
* `governance_lag`
* `cultural_erosion`

These tags can be read as "problem-type" codes: each Case is characterised by a combination of these problem axes.

New tags may be introduced when necessary but should be documented and used consistently.

### 7.2 Awareness and conflict

At Case level, awareness and conflict are assessed through:

* `awareness_level`
* `conflict_intensity`
* `policy_response_level`

These are interpretative assessments based on:

* number and tone of media articles
* presence of protests or local mobilisation
* evidence of political debate
* documented policy responses

The field `assessment_basis` must indicate that the assessment is interpretative or mixed, and `notes` should briefly explain the reasoning.

### 7.3 Problem framing and solutions

`problem_framing` describes how actors explain overtourism:

* `individual` (focus on tourist behaviour)
* `systemic` (broader tourism model)
* `governance` (regulation and institutions)
* `market` (prices, investment, incentives)
* `environmental` (carrying capacity, ecosystems)

`proposed_solutions` stores short textual descriptions of concrete measures proposed in the discourse.

---

## 8. Research Workflow and Source Collection

### 8.1 Identification of destinations and Cases

Destinations and overtourism Cases are identified through:

* local and national media coverage
* academic articles and reports
* NGO and civil society publications
* government and planning documents
* statements by destination marketing organisations and tourism boards
* selected social media content, if attributable to identifiable actors

### 8.2 Source collection and documentation

For each Case and Statement:

* every source must be a real, verifiable document or resource
* at least one clear citation or URL must be stored
* paywalled or print-only sources must have enough bibliographic detail to be relocatable

### 8.3 Explicit rule against fabricated sources and content

There is a strict rule:

* no source, actor, quote, paraphrase or statement may be fabricated
* if a statement or actor cannot be linked to a real source, it must not enter the dataset
* if information cannot be reliably reconstructed, the field remains null

This rule applies equally to manual work and any AI-assisted workflow.

---

## 9. Validation and Integrity Checks

### 9.1 Schema validation

Before release, the dataset must validate against `schema.json`:

* data types must match
* required fields must be present
* no unknown top-level properties should be introduced

### 9.2 ID uniqueness

The following IDs must be unique within the dataset:

* `case_id`
* `actor_id`
* `statement_id`
* `source_id`

IDs are never recycled.

### 9.3 Consistency checks

Checks include:

* every `case_id` referenced in Statements exists in Cases
* every `actor_id` referenced in Statements exists in Actors
* every Statement listed in a Case's `statement_ids` exists and points back to that Case
* `destination_ref.in_main_dataset` is consistent with the presence or absence of `destination_id`

### 9.4 No fabrication rule for AI and automation

All automated or AI-assisted processes must:

* treat schema and methodology as hard constraints
* never invent sources, actors or quotes
* not generalise beyond available evidence
* flag missing information as null instead of guessing

Violating this rule breaks dataset integrity and is not permitted.

---

## 10. Limitations and Bias

The dataset has built-in limitations:

* it is biased toward destinations with visible overtourism discourse
* it does not measure global prevalence of overtourism
* it is limited by language coverage and source availability
* social media is used cautiously and only when attribution is strong

The dataset is best used for:

* qualitative case comparison
* governance pattern analysis
* identification of intervention and partnership opportunities
* exploration of PPP scenarios around overtourism management

---

## 11. Versioning

Dataset ID:

`MARTIN_SAMBAUER_OVERTOURISM_NPLUS1_V1`

Future versions may add:

* more destinations and Cases
* extended actor typologies
* refined taxonomies for solutions and governance instruments
* additional collections for complex source management

Major schema changes will be documented in `dataset_meta.version_notes` and reflected here.

---

## 12. File Naming

The primary JSON data file for this n+1 overtourism discourse layer is named:

`Overtourism_Signal.json`

This naming follows the same convention as `Immersive_Destination_Analysis.json` and allows both datasets to coexist in a consistent namespace.

---

## 13. Reference to Core Dataset (n)

Core dataset: **Immersive_Destination_Analysis**

Repo: [https://github.com/martin-sambauer/immersive-datasets/tree/main/datasets/Immersive_Destination_Analysis](https://github.com/martin-sambauer/immersive-datasets/tree/main/datasets/Immersive_Destination_Analysis)
Raw Data: [https://raw.githubusercontent.com/martin-sambauer/immersive-datasets/main/datasets/Immersive_Destination_Analysis/Immersive_Destination_Analysis.json](https://raw.githubusercontent.com/martin-sambauer/immersive-datasets/main/datasets/Immersive_Destination_Analysis/Immersive_Destination_Analysis.json)
Data File: [https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/Immersive_Destination_Analysis.json](https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/Immersive_Destination_Analysis.json)
README.md: [https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/README.md](https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/README.md)
Methodology.md: [https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/methodology.md](https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/methodology.md)
Schema.json: [https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/schema.json](https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/schema.json)

---

## 14. Explore and Licensing

Explore: repository folder · JSON · [https://martin-sambauer.com/origins-of-wonder-an-immersive-impact-investment/overtourism-signal](https://martin-sambauer.com/origins-of-wonder-an-immersive-impact-investment/overtourism-signal)
Licensing: CC BY 4.0 · © Martin Sambauer · martin-sambauer.com
