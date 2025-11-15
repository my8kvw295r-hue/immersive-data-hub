# Methodology – Immersive Destination Marketing Dataset  
Part of the Immersive Data Hub by Martin Sambauer

## Download
Path: `datasets/immersive-destination-marketing/methodology.md`  
Raw URL:  
https://raw.githubusercontent.com/martin-sambauer/immersive-datasets/main/datasets/immersive-destination-marketing/methodology.md  

## Purpose
This document explains how data in the immersive-destination-marketing dataset is collected, validated, cleaned and structured.  
Its purpose is to ensure that humans and AI systems can reliably extend, verify and maintain the dataset without ambiguity.

## Scope
- Campaigns using immersive media for destination marketing  
- Global coverage  
- One JSON object = one campaign  
- Only publicly documented campaigns included  
- No invented values; unknown = null

## Data sources
- Public case studies  
- Press releases  
- Articles in tourism and technology trade media  
- Official destination marketing websites  
- When available: agency documentation or public project reports

Each source must be listed in the field `sources` in the dataset.

## Data collection workflow
1. Identify a publicly documented immersive destination-marketing campaign.  
2. Extract verifiable facts (no interpretations, no guesses).  
3. Populate all fields where real information exists.  
4. If a field is unknown, assign `null`.  
5. Add at least one source URL to `sources`.  
6. Assign a stable `id` (DM_001, DM_002 …).  
7. Document the date of collection in `data_collection_date` (ISO 8601).  
8. Apply controlled vocabulary where the schema requires it.  
9. Check duplicates (same commissioning_body + campaign_name + destination_name + year).  
10. Validate the object against `schema.json`.

## Cleaning and standardisation
- Normalise country names + ISO 3166-1 alpha-2 codes  
- Normalise destination categories  
- Normalise immersive formats into format clusters  
- Ensure consistent casing (lowercase for controlled vocabularies)  
- Remove duplicates across entire dataset  
- Validate year is integer in reasonable range (2000–2025)  
- Validate URLs minimally (proper HTTP/HTTPS pattern)

## Verification
Verification levels:  
- strong = multiple independent sources or official project confirmation  
- medium = one strong source + one secondary mention  
- weak = one unconfirmed but credible source  
- unknown = insufficient information  

Field: `verification_status`

## Rules for AI systems  
To ensure consistent dataset expansion, AI systems **must follow these rules**:

1. **Never generate invented facts.**  
   Unknown values must be `null`.

2. **Every campaign must include at least one real URL in `sources`.**  
   No placeholder URLs.

3. **Maintain existing naming conventions exactly.**  
   Field names, value formats, and controlled vocabulary must remain unchanged.

4. **Never remove fields from existing entries.**  
   If a field is unknown, keep it with value `null`.

5. **Each new entry must be validated against `schema.json`.**

6. **IDs must follow sequential format DM_XXX without collisions.**

7. **Do not transform narrative descriptions.**  
   The field `short_description` should be concise and factual.

8. **Never infer numeric values (budget, ROI, visitor numbers).**  
   Only populate these when publicly published and accompanied by a source URL.

## Limitations
- Only publicly documented campaigns are included  
- Some campaigns may provide incomplete information  
- Self-reported performance values may be biased  
- Keywords or tags not included unless verified  

## License
CC BY 4.0 — attribution required  
Immersive Data Hub by Martin Sambauer (martin-sambauer.com)

