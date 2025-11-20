## Immersive Tourist Flow Gateways

This dataset documents global projects that use immersive media to guide, redirect, modulate, or replace tourist flows. It focuses on gateway infrastructures such as airports, marinas, mobility hubs, visitor centres, and virtual pre-visit layers designed to influence behaviour before guests enter sensitive environments.

The dataset is based on the methodology defined in *Immersive Tourist Flow Gateways Methodology* and on the conceptual framework described in the article [“Origins of Wonder – An Immersive Impact Investment”](https://martin-sambauer.com/origins-of-wonder-an-immersive-impact-investment/).

## Purpose

The dataset enables systematic comparison of immersive flow-navigation strategies. It supports:

* understanding how immersive storytelling influences visitor behaviour,
* identifying techniques that redirect flows to alternative attractions,
* mapping methods used to shift activity into different timeslots,
* analysing projects that replace fragile physical visits with immersive substitutes,
* tracking conservation-driven visitor guidance systems across the world.

## What the Dataset Contains

Each project entry includes:

* project_id (ascending internal identifier in the form ITFG_0001, ITFG_0002, … stored as a string),
* gateway_type (spatial role of the gateway, e.g. airport_gateway, ecological_gateway, heritage_gateway, marine_gateway, urban_icon_gateway),
* project_goal (flow_redirection, timeslot_shift, behaviour_change, physical_impact_replacement, educational_priming, conservation_support, arrival_expectation_setting, behavioural_priming_only),
* methods_used (routing, priming, temporal redistribution, narrative interventions and other flow-navigation methods described in the methodology),
* media_format (fulldome, 360_degree_projection, virtual_reality, augmented_reality, mixed_reality, spatial_audio_environment, digital_twin_simulation, projection_mapping, interactive_installation, interactive_exhibition, immersive_theatre, AV_show, VR_experience, guided_tour, ride_experience, soundscape_experience),
* intervention_archetype (one or more high-level archetypes such as behaviour_priming_gateway, immersive_substitution_hub, logistics_flow_hub, emotional_peak_gateway, intro_context_gateway),
* problem_fit (list of overtourism problem-types the project addresses, aligned with the Overtourism N+1 issue-tag taxonomy),
* implementation_stage (concept, planned, under_construction, operating, discontinued, unknown),
* commissioning_authority and, where documented, the responsible manager/contact at the authority,
* producer_operating_entity, director/lead_creator and creative/technical partners,
* budget, visitor_capacity_per_hour, annual_visitors, duration_min (where reliably documented),
* sustainability_context (biodiversity, emissions, ecological standards),
* measurable_effects and available effectiveness studies,
* timestamped verification fields (date_added, date_last_verified, source_last_checked),
* source links for every data point.

Unknown fields remain empty until reliable sources are found.


## Intervention Archetypes and Problem Fit

To make the dataset interoperable with the Overtourism N+1 dataset, each project can be annotated with:

* one or more **intervention archetypes** (behaviour_priming_gateway, immersive_substitution_hub, logistics_flow_hub, emotional_peak_gateway, intro_context_gateway), and
* a set of **problem-fit tags** that mirror the overtourism problem-types (e.g. water_stress, infrastructure_overload, plastic_pollution, housing_pressure, governance_lag).

This makes it possible to analyse which gateway logics are used for specific overtourism problem clusters and where immersive interventions are still missing.


## ID Convention

project_id is an internal ascending identifier for each project, formatted as ITFG_ followed by four digits, for example:

* ITFG_0001
* ITFG_0002
* ITFG_0003

Core rules:

* Unique: every project receives a unique ID.
* Ascending: new projects get the next available number (ITFG_0004, ITFG_0005, …).
* Never reused: IDs of removed projects stay retired.
* Stored as string: in JSON and CSV the ID is always stored as a string, preserving leading zeros.

All semantic information about a project (name, location, media formats, gateway type, etc.) is kept in the other fields such as project_name and country.

## Philosophy

The dataset assumes that immersive gateways are not entertainment add-ons but behavioural and infrastructural tools. They can:

* shift desire away from high-impact zones,
* set expectations at arrival,
* function as ecological filters,
* relocate emotional peaks to controlled environments,
* prepare visitors for sensitive ecosystems using narrative priming.

This perspective follows the argumentation in the *Origins of Wonder* article: immersive experiences can decouple emotion from footprint and thereby support sustainable destination management.

## File Structure

* data/ — JSON and CSV versions of the dataset
* methodology.md — detailed research and classification method
* README.md — this document
* schema.json — JSON schema definition for a single project entry

## Reliability

* No hallucinated data
* Every field must be backed by verifiable non-AI sources
* Timestamped verification for transparency
* Projects without evidence are not included

## Explore and Licensing

Explore. repository folder · JSON · article with insights
Licensing. CC BY 4.0 · © Martin Sambauer · martin-sambauer.com
