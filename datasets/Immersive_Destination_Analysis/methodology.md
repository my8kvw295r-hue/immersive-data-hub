# Methodology

## 1. Scope
This dataset captures multi-layered information for global tourism destinations, with emphasis on the **Global South**. It includes:
- tourism throughput,
- investment conditions,
- economic indicators,
- environmental/sustainability factors,
- attractions and bottleneck analysis,
- real estate structures,
- tax and governance layers.

## 2. Data Structure Principles
Each destination follows a common JSON schema:
- `core` – identity & classification  
- `tourism` – arrivals, taxes, stay durations  
- `economy` – wages, GDP, investment climate  
- `throughput_nodes` – airports, ports, stations  
- `real_estate` – pricing normalized to USD  
- `sustainability_profile` – environment & policies  
- `attractions` – metadata & throughput  
- `meta` – timestamps & source references  

**Money objects** use this normalized structure:
```
{
  "amount_local": ...,
  "currency_local": "...",
  "amount_usd": ...,
  "fx_rate_to_usd": ...,
  "fx_rate_date": "YYYY-MM-DD"
}
```

## 3. Data Sources
The following source types are used:
- national statistics bureaus,
- airport and port authorities,
- UNWTO reports,
- World Bank datasets,
- environmental impact studies,
- academic throughput studies,
- tourism tax legislation,
- local real estate portals.

All extracted information includes:
- clear numerical values (no strings),
- normalized monetary values,
- null values where no data is available,
- derivation notes if values are modeled or approximated.

## 4. Throughput Modeling
Throughput of attractions includes:
- licensed daily visitor caps,
- seasonal variations,
- modeled estimates based on:
  - peak counts,
  - known capacity limits,
  - tour operator reports,
  - protected area rules,
  - historical ticket numbers.

Uncertain values include `"throughput_data_quality": "modelled"` or `"unknown"`.

## 5. Global South Emphasis
The project concentrates on:
- Africa,
- Latin America,
- Southeast Asia,
- MENA,
- island and archipelago nations.

A limited number of Global North reference locations may be included for benchmarking.

## 6. Use Cases
### For immersive media producers
- identify high-impact storytelling environments,
- match throughput potential with dome/VR/AR installations,
- evaluate sustainability constraints.

### For investors
- compare destinations via unified metrics,
- understand tourism dependency,
- analyze real estate dynamics,
- assess political stability and environmental risk.

### For research & journalism
- provide structured, transparent, citation-friendly data.

## 7. Versioning
Dataset version: **MARTIN_SAMBAUER_GLOBAL_SOUTH_V1**

Updates include:
- expanded locations,
- improved throughput modeling,
- added socio-economic layers,
- more granular attraction metadata.



## 9. Data integrity, validation and ID rules

To avoid schema drift, hallucinated content and duplicate structures, all future extensions of this dataset MUST follow these rules:

- No fabricated or hallucinated data  
  - All numbers, classifications and textual claims must be backed by real, verifiable sources (see section 3).  
  - If no reliable source is available, the value MUST be set to `null` and accompanied by `throughput_data_quality`, `comment` or `derivation_notes` that transparently flag the limitation (e.g. `"unknown"`, `"modelled"`).  
  - Under no circumstances may values be invented to “fill gaps”.

- No content duplicates  
  - Destinations, attractions, throughput nodes and sources must not be duplicated under different IDs or labels.  
  - If the same real-world entity appears again (e.g. the same national park or airport), the existing ID MUST be reused and referenced instead of creating a new one.

- ID strategy and numbering  
  - `destination_id`, `attraction_id`, `hub_id` (airports/ports) and any other IDs must be unique within their respective namespace.  
  - Where numeric or sequence-based IDs are used (e.g. `DEST_001`, `ATT_001`), numbering MUST be strictly forward-only and without reuse:  
    - no gaps introduced by deletion followed by reuse,  
    - no collisions or duplicate IDs across the dataset.  
  - Any automated or AI-assisted data generation must treat ID creation as a critical operation and validate uniqueness before writing.


- Destination ID generation (`destination_id`)
  - Format: `DEST_01`, `DEST_02`, `DEST_03`, … (prefix `DEST_` plus zweistellige, aufsteigend vergebene Nummer).
  - Reihenfolge: Die Nummer wird ausschließlich aus der Position im `destinations[]`-Array abgeleitet (erste Destination = `DEST_01`, zweite = `DEST_02` usw.).
  - Keine Semantik: Die ID trägt keine Bedeutung zu Region, Priorität oder Wichtigkeit; sie dient nur als stabile, technische Referenz.
  - Neue Destinationen werden immer am Ende des Arrays angehängt und erhalten die nächste freie Nummer (z.B. nach `DEST_19` folgt `DEST_20`).
  - IDs werden niemals recycelt. Wenn eine Destination entfernt wird, bleibt ihre ID dauerhaft unbenutzt.
  - Eine vollständige Neunummerierung aller Destinationen ist nur im Rahmen eines Major Releases (z.B. v1 → v2) erlaubt und muss in `dataset_meta.version_notes` dokumentiert werden.


- Validation workflow  
  - Every commit or dataset release must be checked against `schema.json`.  
  - A separate validation step must ensure that:  
    - all IDs are unique,  
    - no duplicated content records exist for the same entity,  
    - all money objects and key indicators either contain real sourced values or `null` with a clear explanation.  

These rules are binding for manual editing, scripted imports and AI-assisted extensions of the dataset.

- Destination counts  
  - The number of destinations in any dataset file is always determined by the length of the top-level `destinations[]` array.  
  - Earlier dataset versions exposed `meta_instructions_for_ai.expected_collections.destinations_count` as a helper field; this has been removed to avoid drift between hard-coded counts and the actual array length.

## 8. Attribution
Use this citation:

**Sambauer, Martin (2025)**  
Global South Tourism & Investment Dataset (MARTIN_SAMBAUER_GLOBAL_SOUTH_V1), CC BY 4.0.  
https://originofwonder.com
