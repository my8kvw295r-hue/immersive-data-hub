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
* gateway type (airport, marina, urban, ecological, virtual),
* project goals (flow redirection, behaviour change, substitution, etc.),
* methods (routing, priming, temporal redistribution, narrative interventions),
* media formats (fulldome, VR, AR, projection, digital twin),
* commissioning authority and, where documented, the responsible manager/contact at the authority,
* production entities (producers, operators, creators, directors),
* capacity data, visitor metrics, duration, budget (when available),
* sustainability context (biodiversity, emissions, ecological standards),
* measurable effects and available effectiveness studies,
* timestamped verification fields,
* source links for every data point.

Unknown fields remain empty until reliable sources are found.

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
