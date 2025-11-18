# Overtourism n+1 Dataset – README

This repository contains the **Overtourism n+1 Dataset**, a global qualitative discourse and stakeholder layer designed to complement the structural core dataset **Immersive_Destination_Analysis (n)**.

The n+1 dataset focuses exclusively on **documented overtourism discourse**, including conflicts, governance responses, NGO activity, stakeholder perspectives, and media pressure.

---

## Purpose

The dataset enables:

* analysis of overtourism discourse across destinations
* identification of key actors and institutions
* mapping of NGO involvement and pressure
* assessment of media visibility and conflict intensity
* evaluation of tourism dependency levels
* discovery of intervention opportunities for immersive communication
* support for impact‑driven destination stewardship strategies

The dataset is **not globally representative**. It is intentionally biased toward destinations where overtourism is explicitly discussed in public sources.

---

## Data File

Primary dataset file:

**Overtourism_Signal.json**

This file contains three collections:

* `cases`
* `actors`
* `statements`

together representing the full overtourism discourse for each destination.

---

## Structure Overview

### 1. Cases

Each Case corresponds to one destination and includes:

* destination linkage (to n dataset when available)
* issues and conflict fields
* awareness and policy response levels
* NGO pressure level
* media pressure level
* tourism dependency category
* research window
* associated statement IDs
* meta information and key sources

### 2. Actors

Actors include individuals and organisations such as:

* government representatives
* destination managers and sustainability managers
* NGOs
* residents and activist groups
* tourism businesses and operators
* researchers and experts

Institutional metadata may include supervising ministries, budgets (if documented), and timestamps.

### 3. Statements

Statements represent individual contributions to the discourse and include:

* source metadata (title, URL, publisher, dates)
* quote (if permissible)
* English paraphrase
* issue coding, problem framing, proposed solutions
* stance, tone and calls for action
* relevance for immersive interventions

---

## Taxonomies

The dataset uses controlled vocabulary for:

* media pressure (None, Low, Mid, High, Extreme)
* NGO pressure (None, Low, Mid, High, Extreme)
* tourism dependency (Low to Extreme)
* issue tags, used as problem‑type codes at Case and Statement level. Recommended tags include:

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


---

## Research and Source Requirements

All content must be based strictly on **real, verifiable sources**.
No fabricated actors, quotes, NGOs, documents or issues are permitted.

Sources include:

* local and national media
* academic papers
* NGO reports
* government documents
* identifiable social media statements

Every statement must have a complete source object with access timestamp.

---

## Interoperability with the Core Dataset (n)

When destinations exist in **Immersive_Destination_Analysis**, Cases reference them via:

* `destination_ref.destination_id`
* `destination_ref.destination_name`
* `in_main_dataset = true`

External enrichment destinations use:

* `destination_id = null`
* `in_main_dataset = false`
* optional `candidate_for_main_dataset = true`

Core dataset links:

Repo: [https://github.com/martin-sambauer/immersive-datasets/tree/main/datasets/Immersive_Destination_Analysis](https://github.com/martin-sambauer/immersive-datasets/tree/main/datasets/Immersive_Destination_Analysis)
Raw Data: [https://raw.githubusercontent.com/martin-sambauer/immersive-datasets/main/datasets/Immersive_Destination_Analysis/Immersive_Destination_Analysis.json](https://raw.githubusercontent.com/martin-sambauer/immersive-datasets/main/datasets/Immersive_Destination_Analysis/Immersive_Destination_Analysis.json)
Data File: [https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/Immersive_Destination_Analysis.json](https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/Immersive_Destination_Analysis.json)
README.md: [https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/README.md](https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/README.md)
Methodology.md: [https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/methodology.md](https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/methodology.md)
Schema.json: [https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/schema.json](https://github.com/martin-sambauer/immersive-datasets/blob/main/datasets/Immersive_Destination_Analysis/schema.json)

---

## Schema

The exact structure is defined in:

**schema.json**

This schema ensures:

* consistency across Cases, Actors, and Statements
* correct typing
* completeness of required fields
* enforcement of taxonomies and controlled lists

---

## Versioning

Current dataset version:

`MARTIN_SAMBAUER_OVERTOURISM_NPLUS1_V1`

Future releases may extend actor typologies, add new cases, refine taxonomies, or introduce additional collections for complex source management.

---

## Article

Background and conceptual foundation for this dataset are described here:

[https://martin-sambauer.com/origins-of-wonder-an-immersive-impact-investment/](https://martin-sambauer.com/origins-of-wonder-an-immersive-impact-investment/)

### Conceptual Synopsis

The article outlines how immersive media can serve as a strategic response to overtourism pressures by shifting visitor behaviour, redistributing flows, and strengthening local stewardship. It introduces the idea that destinations under pressure require new forms of communication capable of conveying complexity, emotional resonance, and carrying-capacity awareness. This forms the philosophical basis for the n+1 dataset: overtourism discourse reveals where immersive interventions could support sustainable tourism futures.

---

## Explore and Licensing

Dataset background and conceptual foundations are described here:

[https://martin-sambauer.com/origins-of-wonder-an-immersive-impact-investment/overtourism-signal](https://martin-sambauer.com/origins-of-wonder-an-immersive-impact-investment/overtourism-signal)

---

## Explore and Licensing

Explore: repository folder · JSON · article with insights
Licensing: CC BY 4.0 · © Martin Sambauer · martin-sambauer.com
