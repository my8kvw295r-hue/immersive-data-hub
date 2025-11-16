# Immersive Destination Analysis – Global South Tourism and Investment Destinations

This dataset describes a curated set of tourism destinations with high relevance for immersive experiences, experiential travel and long-term place-making. It combines basic tourism, demographic and economic indicators with fields that are explicitly designed for immersive media strategy and destination storytelling.

The current version is a pilot with a limited but growing set of destinations. The dataset does not hard-code the total number of destinations in the metadata. Instead, any user or AI agent should derive the current count directly from the length of the `destinations` array in the JSON file.

The dataset is curated and maintained by Creative Director Martin Sambauer (martin-sambauer.com).

  
## Ontology context

This dataset is part of the immersive-datasets repository and follows the ontology described in `/ontology.md`.

In that ontology, destinations are treated as one layer in a wider immersive ecosystem:

- destinations as nodes where immersive experiences and tourism flows meet
- investors and funding streams as a second layer that can be connected to these nodes
- skills, roles and immersive qualities as a third layer that describes which teams and formats are best suited for a given place
- media formats (fulldome, XR venues, location-based experiences) as the operational layer that turns destinations into stories and experiences

Within this ontology, `Immersive_Destination_Analysis` is the layer that answers questions like:

- which destinations in the Global South are structurally attractive for immersive projects?
- where do tourism flows, real estate, infrastructure and sustainability profiles create fertile ground for immersive experiences?
- which destinations are promising candidates for future cross-analysis with investors and creative talent datasets?

Future stacked datasets can link this destination layer to:

- investor datasets (for example: Gulf or wider MENA investors in immersive projects)
- immersive skill and role taxonomies
- catalogues of immersive qualities and project features


## Dataset contents

The JSON file `Immersive_Destination_Analysis.json` contains the following top-level keys:

- `dataset_meta`  
  Basic metadata (title, description, version, timestamps, license).

- `destinations`  
  An array where each element describes a single destination, combining:
  - core identity (name, country, region, income level, tourism dependency)
  - tourism flows and basic fiscal parameters
  - economic and real-estate context
  - sustainability and environmental constraints
  - attractions and throughput nodes relevant for immersive experiences
  - an investor-oriented profile block

- `meta_instructions_for_ai`  
  Guidance for LLMs and agents on how to interpret and extend the dataset without hallucinating additional entries.

- `data_contract`  
  Structural expectations (required fields, value ranges, naming conventions) to support automated validation and future stacked datasets.


## Key results from pilot version V19

The following points summarise what can already be seen in the current 19-destination pilot, before any extended statistical analysis or stacked datasets:

1. Global South focus with two reference benchmarks  
   17 of the 19 destinations are located in the Global South. Two destinations (Athens Metropolitan Area and Yellowstone National Park) are intentionally included as reference locations for benchmarking against a European metro region and a North American national park.

2. Strong concentration in upper-middle-income countries  
   Income level distribution (World Bank categories) in this pilot:
   - 9 destinations in upper-middle-income economies  
   - 5 in lower-middle-income economies  
   - 1 in low-income  
   - 4 in high-income (including the reference cases)  
   This reflects an early focus on places where tourism is already a key economic driver and where immersive investments can realistically scale.

3. Tourism giants vs. high-value niche destinations  
   Based on the maximum recorded yearly visitor counts in the tourism profiles:
   - Dubai leads the set with around 17.15 million international visitors  
   - Cancún & Riviera Maya follow with about 12.5 million visitors  
   - Punta Cana, Halong Bay, Bali and Abu Dhabi also sit in the multi-million range  
   At the same time, the dataset includes smaller, high-value or fragile sites like Galapagos, Petra or the Okavango Delta, which are strategically important for low-volume, high-impact immersive storytelling.

4. Tourist taxation as a design parameter for visitor experience  
   In 12 out of 19 destinations, a formal tourist tax or equivalent levy applies (per entry, per room night, environmental fee or mixed models). The forms range from:
   - protected area entry fees and bay fees  
   - hotel-based room-night taxes (Tourism Dirham in Dubai, Visitax models etc.)  
   - hybrid systems that combine entry, control cards and accommodation taxes  
   For immersive strategy, this is a signal that these destinations already operate with a fiscal logic around visitors, which can influence pricing, ticketing and positioning of immersive experiences.

5. Multiple world regions, but a clear MENA and Latin America emphasis  
   The sample covers several regions:
   - Latin America and the Caribbean (including Galapagos, Cartagena, Cancún & Riviera Maya, etc.)
   - Sub-Saharan and pan-African destinations (including East Africa and wetland ecosystems)
   - MENA hubs such as Dubai and Abu Dhabi
   - selected Southeast Asian hotspots  
   This spread is intentional: it creates a first grid where later investor datasets (for example Gulf, sovereign or family office investors) can be mapped to concrete territories.

6. Built for future cross-analysis with investors and skills  
   Each destination already includes an `investor_profile` section, even if populated at a basic level in this pilot. The structure is designed so that:
   - future investor datasets can link directly to destinations through thematic, risk and region alignment
   - skill and role datasets (for example, the Creative Directors for Immersive Media taxonomy) can be matched to destination types (ecotourism, coastal resort, heritage city, mega resort, etc.)
   - later “stacked datasets” can identify where destination characteristics, investor appetite and available immersive skill pools overlap.

These key results are deliberately high-level. They are intended to guide future statistical deep dives and to inform articles, whitepapers and content pieces derived from the dataset.


## Fields and structure

Each element in the `destinations` array uses the following main blocks:

- `destination_id`  
  Stable identifier such as `DEST_01`, `DEST_02`, … `DEST_19`.

- `core`  
  - `destination_name`  
  - `destination_type` (archipelago_province, metro_region, protected_area, resort_region, etc.)  
  - `country_name`, `country_iso2`  
  - `global_south_flag`  
  - `world_region`  
  - `world_bank_income_level`  
  - `tourism_dependency_category`  
  - `main_city_name`, `main_city_population_estimate`, `main_city_population_year`

- `tourism`  
  - `yearly_profiles` with:
    - `year`
    - `total_visitors_all_segments`
    - optional fields such as `avg_length_of_stay_nights`, `overnight_stays_total`, `tourism_revenue_total`
  - `international_tourist_arrivals` (where available as a separate series)
  - `tourist_tax` block with:
    - `tourist_tax_applies`
    - `tourist_tax_main_type`
    - `tax_items` (amount, currency, unit, FX metadata)

- `economy`  
  - GDP and sectoral context (where available)
  - tourism share in GDP where documented
  - notes useful for investment and policy framing

- `throughput_nodes`  
  - airports, cruise ports, land border crossings or central mobility hubs
  - indicators of connectivity and visitor throughput relevant to immersive experiences

- `real_estate`  
  - basic signals for hotel stock, resort development, large-scale leisure infrastructure
  - placeholders for future detailed fields such as pipeline projects, mixed-use districts, etc.

- `sustainability_profile`  
  - environmental constraints (fragile ecosystems, UNESCO status, national park protections)
  - climate and biodiversity considerations relevant to sustainable immersive experiences

- `attractions_meta` and `attractions`  
  - structured overview of the main attraction types (natural wonders, heritage sites, resort clusters, theme experiences)
  - individual entries with narrative cues for immersive storytelling

- `investor_profile`  
  - indicative fit with different investor archetypes (sovereign funds, tourism development funds, private equity, family offices)
  - risk and opportunity framing for immersive and experiential projects  

- `meta`  
  - notes, sources, caveats at destination level


## Methodology

This pilot version was compiled through:

1. Manual research  
   Tourism statistics, official reports, destination marketing materials, development agency documents and press articles were collected and cross-checked where possible.

2. Structured extraction and normalisation  
   Key figures for visitor numbers, basic demographics and taxation were mapped into a consistent field structure. When exact values were not available, fields were left null rather than approximated.

3. Immersive-oriented modelling  
   Additional blocks (`throughput_nodes`, `attractions_meta`, `investor_profile`) were designed to support immersive media strategy, not just tourism analysis. These blocks favour qualitative and categorical signals that are useful for creative direction and investor conversations.

4. Data contract and AI instructions  
   `data_contract` and `meta_instructions_for_ai` were added to:
   - minimise hallucinations when LLMs work with the JSON
   - keep schema evolution under control as the dataset grows
   - make it easier to connect this dataset to other layers in the repository

Further technical details and the overall conceptual framing are documented in `/ontology.md` and in the root README of the immersive-datasets repository.


## Limitations and planned extensions

- Pilot scale  
  This is a curated pilot set, not an exhaustive global list of destinations.

- Partial numeric coverage  
  For some destinations, only headline visitor numbers are currently populated. Length of stay, revenue and detailed segmentation are not yet consistently available.

- Evolving investor profile fields  
  The `investor_profile` block is still in its early phase and will be refined once dedicated investor datasets (for example: Arab immersive investment funds) are added to the repository.

Planned next steps include:

- adding more destinations in the Global South with high immersive potential
- enriching economic and real-estate fields
- aligning destination typologies more tightly with immersive formats (fulldome, XR venues, themed media architecture)
- preparing stacked datasets that connect this destination layer to investors and skill taxonomies


## Suggested use cases

Typical uses of this dataset include:

- identifying promising destinations for immersive experience concepts and feasibility studies
- supporting destination marketing strategies with structured tourism and place-making data
- building narratives and whitepapers about immersive tourism in the Global South
- feeding AI agents that recommend potential matches between destinations, investors and creative teams
- benchmarking specific destinations against a small, carefully curated peer group


## Citation

If you use this dataset in research, presentations, journalism or strategy work, please include an attribution such as:

Immersive Destination Analysis – Global South Tourism and Investment Destinations (Pilot V19), curated by Martin Sambauer (martin-sambauer.com). Part of the immersive-datasets repository. Licensed under CC BY 4.0.
