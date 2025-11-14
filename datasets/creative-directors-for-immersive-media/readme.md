# Creative Directors in Immersive Media – Global Dataset (1950–2025)

This repository hosts the **Creative Directors in Immersive Media – Global Dataset**, a machine-readable collection of individuals working in the field of immersive media, immersive events, fulldome cinema, XR, experiential architecture, and large-scale media environments.

The dataset is part of a long-term research project to map the evolution of immersive media creative direction from the 1950s to the present.  
It accompanies the article *Creative Directors in Immersive Media: A Global Overview (1950–2025)* published at:

https://martin-sambauer.com

## Purpose of the Dataset

Immersive media has established itself as a global field spanning:

- multiscreen and expanded cinema  
- media art and interactive installations  
- fulldome and large-format storytelling  
- VR / XR and spatial cinema  
- LED stages and immersive arenas  
- corporate immersive experiences  

Yet there has never been a structured, global overview of the individuals who shape this field.

This dataset aims to:

- document creative directors, artists, designers and producers working in immersive media  
- provide a historical arc (1950–2025)  
- classify individuals across multiple clusters and domains  
- offer a machine-readable reference for researchers, curators, festivals and institutions  
- support long-term analysis of trends, technologies and professional roles in immersive media  

The dataset is not a ranking and not a complete list. It is an evolving research corpus.

## Dataset Structure

All data is stored in:

```
/datasets/immersive-creative-directors/
    creative_directors_global.json
    creative_directors_global.schema.json  (optional)
    methodology.md
    changelog.md
```

The main file is `creative_directors_global.json`.

Each entry follows this structure:

```
{
  "name": "First Last",
  "country": "Country",
  "birth_year": 1977,
  "roles": ["Creative Director", "XR Artist"],
  "focus_areas": ["VR", "Fulldome", "Immersive Theatre"],
  "notable_works": ["Work A", "Work B"],
  "affiliations": ["Studio or Institution"],
  "links": {
    "website": "https://example.com",
    "instagram": "https://instagram.com/example",
    "imdb": "https://imdb.com/name/example"
  }
}
```

## How the Dataset Was Created

### 1. Definition of Scope (1950–2025)
Historical field definition from avant-garde to XR stages and immersive brand experiences.

### 2. Establishing Conceptual Clusters
Classification clusters:

- analog_media_art_pioneers  
- digital_interactive_pioneers  
- immersive_installations  
- fulldome_large_format  
- vr_xr_creators  
- live_immersive_stages / large_scale_live_shows  
- corporate_brand_immersive  

### 3. Selection of Individuals
Natural persons with verifiable public work in immersive media.

### 4. Verification Through Public Sources
Every entry has at least one source (festivals, museums, planetariums, academic profiles, studio pages, press releases).

### 5. JSON Normalization
Consistent types, formats, arrays and unique `cdim_XXXX` IDs.

### 6. Duplicate Removal and Replacement
Duplicates merged; unsourced entries replaced with fully referenced individuals.

### 7. Systemic Integrity Check
Ensured valid references, unique IDs/names, working links, schema conformity.

### 8. Compatibility With Other Datasets
Interlinked with:

- Immersive Market Participants  
- Immersive Venue & Planetarium Dataset  
- Immersive Keywords Dataset  

## License

**Creative Commons Attribution 4.0 International (CC BY 4.0)**  
https://creativecommons.org/licenses/by/4.0/

Attribution required:  
*“Creative Directors in Immersive Media – Global Dataset (1950–2025), curated by Martin Sambauer – https://martin-sambauer.com”*

## Versioning

Logged in `changelog.md`:

- MAJOR – structural changes  
- MINOR – new individuals, expanded clusters  
- PATCH – corrections, metadata fixes  

## Contributing

Contributions via pull request are welcome.

## Maintainer

**Martin Sambauer**  
Creative Director for Immersive Media  
https://martin-sambauer.com
