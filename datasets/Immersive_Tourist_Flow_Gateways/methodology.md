## Methodology for the Dataset

This methodology defines how projects are researched, validated, classified, and recorded for the dataset Immersive_Tourist_Flow_Gateways. The goal is to document immersive gateway systems that guide, redirect, modulate, or replace tourist flows using spatial storytelling, behavioural cues, and technological interventions. The approach is directly aligned with the framework described in the article on martin-sambauer.com about Origins of Wonder.

## 1. Scope

A project qualifies for inclusion if it uses immersive media or spatial interventions to:

* redirect or re-route tourist flows to alternative attractions or zones,
* shift tourist activity into different time windows or timeslots,
* replace the physical visit through immersive substitution experiences,
* influence behaviour before entering sensitive or high-impact areas,
* act as a functional gateway (airport, marina, visitor centre, mobility hub, digital twin),
* create emotional peaks away from fragile environments.

Included:

* immersive arrival experiences,
* visitor centres with immersive flow-management goals,
* dome theatres used as behavioural or routing tools,
* XR-based ecological or cultural behaviour-change experiences,
* virtual pre-visit layers designed to prime expectations and reduce impact.

Excluded:

* attractions without any influence on flow navigation,
* museums without gateway role,
* purely promotional installations without behavioural or structural intent.

## 2. Research Principles

### 2.1 Evidence Requirement

Each entry must be backed by at least one verifiable, non-AI source (masterplans, academic papers, government documents, operator announcements, reliable journalism).

### 2.2 Anti-Hallucination Rule

No assumptions or speculative values may be added. Unknown fields remain empty. Every recorded detail must be confirmable.

### 2.3 Timestamping

Each dataset entry includes:

* date_added (UTC),
* date_last_verified (UTC),
* source_last_checked.

These ensure transparency about the dataset’s freshness.

## 3. Taxonomy

### 3.1 Project Goal

* flow_redirection
* timeslot_shift
* behaviour_change
* physical_impact_replacement
* educational_priming
* conservation_support
* arrival_expectation_setting

### 3.2 Methods of Flow Navigation

* immersive substitution (virtual/dome replacing physical visit),
* emotional peak relocation (peak away from sensitive zones),
* content-driven routing (post-experience suggested paths),
* temporal redistribution (encouraging off-peak attendance),
* spatial storytelling as a navigation layer,
* behavioural narrative priming (instructions embedded in story arcs),
* gateway sequencing (multi-step immersive entry funnels).

### 3.3 Media Formats

* fulldome
* 360-degree projection
* virtual reality
* augmented reality
* mixed reality
* spatial audio environments
* digital twins and simulation chambers

### 3.4 Spatial Role

* airport_gateway
* marina_gateway
* urban_gateway
* ecological_gateway
* visitor_centre
* virtual_gateway


### 3.5 Intervention Archetypes

For analytical work, each project is classified into one or more high-level intervention archetypes. These archetypes summarise how the gateway primarily intervenes in visitor flows and behaviours:

* behaviour_priming_gateway – the project focuses on codes of conduct, cultural understanding, and ecological awareness before visitors enter sensitive zones. The physical experience at the site remains largely unchanged; the gateway shapes attitudes and expectations.
* immersive_substitution_hub – the project offers a substantial part of the desired experience as an immersive substitute (e.g. dome, AV theatre, XR). Visitors can satisfy a large portion of their curiosity without going all the way into fragile or remote environments.
* logistics_flow_hub – the gateway is tightly coupled to transport, ticketing, or routing infrastructure (e.g. shuttle systems, mandatory visitor centres, timeslot management) and acts as a physical and organisational filter.
* emotional_peak_gateway – the project relocates the strongest emotional or iconic moment of the destination into the gateway (e.g. 360° Stonehenge room, fjord cinema, aurora dome), thereby reducing pressure on the most sensitive locations.
* intro_context_gateway – the project primarily provides narrative and spatial context (history, geology, ecosystem framing) with light or no explicit flow-control mechanisms.

Projects can carry more than one archetype, but typically one or two dominate.

### 3.6 Problem Fit (Overtourism Problem Types)

To link the gateway dataset to the overtourism problem-space, each project can be annotated with a list of problem-types for which it is a plausible intervention. These problem-types mirror the issue-tag taxonomy used in the Overtourism N+1 dataset, for example:

* water_stress
* infrastructure_overload
* plastic_pollution
* ecosystem_stress
* biodiversity_loss
* housing_pressure
* social_conflict_protests
* ngo_pressure
* governance_lag
* cultural_erosion

This allows later analyses to ask: which intervention archetypes are actually used (or missing) for specific overtourism problem clusters.


## 4. Data Fields

For each project, the dataset records:

* project_id (ascending internal identifier in the form ITFG_0001, ITFG_0002, …, stored as a string and never reused),
* project_name,
* country,
* region,
* gateway_type,
* project_goal,
* methods_used,
* media_format,
* intervention_archetype (one or more high-level intervention archetypes, as defined in section 3.5),
* problem_fit (list of overtourism problem-types for which the project is a plausible intervention, aligned with the Overtourism N+1 issue-tag taxonomy),
* implementation_stage (concept, planned, under construction, operating, discontinued, unknown),
* commissioning_authority (name of the commissioning public body or client institution),
* commissioning_authority_manager (responsible manager or contact person at the commissioning authority, if documented),
* producer / operating_entity,
* director / lead_creator,
* creative studio and technical partners (if documented),
* budget (if documented),
* visitor_capacity_per_hour,
* annual_visitors (if available),
* duration_min,
* sustainability_context (biodiversity, conservation, emissions),
* measurable_effects (if documented),
* measurement_methods_used,
* effectiveness_studies_available (yes/no),
* reference_urls,
* timestamp fields (date_added, date_last_verified, source_last_checked),
* notes where needed for contextual explanations.

Unknown fields remain empty when no reliable, non-AI sources are available.

## 5. ID Convention

project_id is a purely internal identifier used for stable referencing of projects in the dataset, on martin-sambauer.com, and in derivative analyses.

Core rules:

* Prefix + number: every ID starts with ITFG_ followed by a four-digit number (e.g. ITFG_0001, ITFG_0002).
* Ascending: IDs follow a simple increasing sequence (ITFG_0001, ITFG_0002, ITFG_0003, …).
* Stored as strings: in JSON and CSV files, IDs are stored as strings to keep sorting stable and preserve leading zeros.
* Never reused: when a project is deprecated or removed, its ID is retired and never assigned to a different project.
* No semantic content: IDs do not encode location, media format, or year; all meaning stays in the other fields (project_name, country, gateway_type, etc.).

This keeps the dataset easy to merge, version, and reference while avoiding fragile naming schemes.

## 6. Effectiveness Studies and Measurement

A core objective of the dataset is to understand the real influence of immersive gateways on visitor behaviour. Therefore the dataset documents:

### 6.1 Types of Measured Impact

* reduction of traffic to sensitive zones,
* increase in usage of alternative attractions,
* redistribution across timeslots,
* behavioural compliance rates (ecological or cultural),
* visitor awareness uplift scores,
* percentage of visitors choosing immersive substitution instead of physical presence.

### 6.2 Measurement Methods

* controlled studies with control groups,
* post-experience surveys,
* tracking of visitor routing changes,
* ecological impact monitoring,
* ticketing and timeslot data analysis,
* behavioural audits in protected zones,
* qualitative interviews where available.

### 6.3 Scientific Literature

The dataset includes references to:

* XR behaviour-change research,
* immersive conservation storytelling studies,
* overtourism mitigation literature,
* gateway-based flow engineering case studies.

## 7. Alignment with the Origins of Wonder Framework

The methodology follows the principles outlined in the article [Origins of Wonder – An Immersive Impact Investment](https://martin-sambauer.com/origins-of-wonder-an-immersive-impact-investment/):

* emotional peaks can be separated from fragile physical sites,
* immersive story environments can prime behaviour before arrival,
* gateways act as narrative and logistical filters,
* flow management blends ecology and audience experience,
* immersive storytelling can reduce physical pressure while increasing understanding.

## Explore and Licensing

Explore. repository folder · JSON · article with insights
Licensing. CC BY 4.0 · © Martin Sambauer · martin-sambauer.com
