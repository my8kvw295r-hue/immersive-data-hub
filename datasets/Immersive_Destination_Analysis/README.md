# Global South Tourism & Investment Dataset (Immersive Destination Analysis)

## Overview
This repository contains the Global South Tourism & Investment Dataset, curated to support:
- immersive media strategy,
- investor intelligence,
- destination benchmarking,
- throughput and bottleneck analysis.

The dataset is specifically designed as an investment-intelligence layer for immersive destination funds and MENA-based investors who are looking for international flagship projects that push the frontier of experiential tourism, conservation-aligned visitor infrastructure, and immersive media deployment across the Global South and selected benchmark locations. :contentReference[oaicite:0]{index=0}

The dataset contains various destinations and is supposed to grow. It is designed to scale to 40–50 fully researched locations across the Global South.

## Purpose
The dataset provides a structured foundation for:
- identifying high-throughput tourism nodes,
- mapping bottlenecks (airports, ports, attractions),
- evaluating real estate and investment climate,
- understanding sustainability and overtourism pressures,
- providing bot-friendly, citation-friendly open data,
- supporting capital allocation decisions for immersive destination funds and sovereign, private and family-office investors, especially from the MENA region,
- aligning immersive storytelling, domes, VR/AR and experiential infrastructure with concrete throughput, yield and conservation signals at each location. :contentReference[oaicite:1]{index=1}

It will serve as the underlying data layer for articles published on  
https://originofwonder.com and https://martin-sambauer.com

## Target groups
This dataset is built for a mixed ecosystem of creative and financial actors around immersive destinations, including:

- Project developers in tourism, real estate and conservation-led destination development (airport, port, resort and mixed-use projects).
- Immersive and experiential professionals: creative directors, immersive media producers, fulldome and XR studios, spatial storytellers, exhibition designers, architects and experience strategists.
- Investors and fund managers, with a special focus on:
  - MENA-based immersive destination funds,
  - Arab and wider MENA family offices,
  - sovereign and quasi-sovereign vehicles looking for scalable, conservation-aligned experiential assets,
  - global impact and tourism investors seeking data-backed immersive destination theses.


## Data quality and validation principles

This repository is maintained under strict data integrity rules:

- No invented or hallucinated values  
  - All figures, classifications and descriptions must be grounded in real, verifiable sources.  
  - Missing or unreliable data is represented as `null` plus an explicit quality flag or comment (e.g. `"unknown"`, `"modelled"`), never as a guessed value.

- No content duplicates  
  - The same real-world destination, attraction or throughput node must not appear multiple times under different IDs or labels.  
  - Existing IDs are reused; new IDs are created only for genuinely new entities.

- ID uniqueness and numbering  
  - `destination_id`, `attraction_id`, `hub_id` and other IDs must be unique within their namespace.  
  - Where sequence-based IDs are used, numbering must not be reused or duplicated.  

All changes and new locations must validate against `schema.json` and follow the detailed rules in `METHODOLOGY.md` (section 9).


## License
CC BY 4.0  
Attribution required: https://martin-sambauer.com – Martin Sambauer

## File Structure
- `Immersive_Destination_Analysis.json` – the main dataset  
- `README.md` – repository overview  
- `METHODOLOGY.md` – detailed explanation of data collection  
- (future) `/sources/` – raw sources and extraction files  

## Contact
Martin Sambauer  
https://martin-sambauer.com
