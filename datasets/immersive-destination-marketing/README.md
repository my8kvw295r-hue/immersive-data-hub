# Immersive Destination Marketing Dataset

Current snapshot: 88 entries – updated with X (Twitter) user feedback and extended venue/format metadata.

- Main file: `immersive-destination-marketing.json`  
- Readme: `README.md` (this file)

This dataset is a curated sample of immersive destination marketing projects worldwide.  
It focuses on experiences that:

- promote or interpret real-world destinations (cities, regions, countries, attractions, routes), and  
- use immersive media (e.g. flying theatres, domes/planetariums, projection mapping, VR/AR, immersive rooms, game worlds, immersive visitor centres).

The dataset is not exhaustive. Its purpose is:

- qualitative and exploratory analysis  
- making patterns visible (formats, commissioners, venues, audiences, goals)  
- providing real-world examples for strategy, teaching, talks and concept work  

---

## 1. License – CC BY 4.0

This dataset and documentation are licensed under the Creative Commons Attribution 4.0 International (CC BY 4.0) license.

You are free to:

- Share — copy and redistribute the material in any medium or format  
- Adapt — remix, transform, and build upon it, even commercially  

Under the following terms:

- Attribution — Any use must include a credit line such as:  

  > Data and documentation originally compiled by [Martin Sambauer](https://martin-sambauer.com).

  or an equivalent attribution including the name Martin Sambauer and the URL  
  https://martin-sambauer.com

Full license text: https://creativecommons.org/licenses/by/4.0/

If you remix, enrich or extend this dataset, please keep the attribution and clearly mark your own changes (for example in a changelog or version note).

---

## 2. Scope and selection

Projects are included when:

1. They clearly promote or interpret a real place or destination, not just a generic brand.  
2. They use an immersive format beyond a simple flat video or static display.  
3. There is at least one public source describing them (ideally several).

The dataset is intentionally:

- global – covering different regions and tourism markets  
- format-diverse – from domes and projection mapping to VR, games and hybrid experiences  
- mixed in maturity – including long-running attractions, one-off shows and pilot projects  

---

## 3. File format and main fields

The file `immersive-destination-marketing.json` uses a flat JSON array of project objects.  
Each object describes one immersive destination marketing project.

Key fields (simplified overview):

- `id` – internal numeric or string ID, stable within this dataset.
- `project_name` – project or experience title (English where possible, original title in `original_title` if relevant).
- `destination` – main destination promoted (for example “Iceland”, “Dubai”, “Hamburg Port”).
- `destination_level` – rough level (for example `city`, `region`, `country`, `attraction`, `route`).
- `country` – ISO country or descriptive country name primarily associated with the destination.
- `location_city` / `location_country` – where the experience is or was physically located (if different from destination).
- `immersive_format` – main format category, such as:
  - `flying_theatre`
  - `dome_fulldome_planetarium`
  - `projection_mapping`
  - `vr` / `ar` / `mixed_reality`
  - `immersive_room`
  - `game_world` / `metaverse` / `digital_platform`
- `venue_type` – where the project is or was hosted (for example `theme_park`, `museum`, `tourist_attraction`, `expo`, `temporary_pop_up`).
- `commissioner_or_client` – tourism board, city, region, brand or institution that commissioned or supported the project (if known).
- `creator_or_production_company` – main studio, agency or collective behind the project (if known).
- `year_start` / `year_end` – years of operation or premiere; `year_end` may be null for ongoing.
- `status` – for example `planned`, `concept`, `operational`, `closed`, `historic_reference`.
- `short_description` – 1–3 sentences, English, free text.
- `goals` – high-level goals, for example `destination_branding`, `visitor_attraction`, `expo_showcase`, `cultural_promotion`.
- `target_audiences` – rough audience groups (for example `families`, `tourists`, `trade_visitors`, `students`).
- `sources` – list of URLs used as evidence (press, project pages, videos, articles).

Additional fields may include:

- `offsite_destination_promotion` – whether the experience promotes a destination different from its physical location (true/false).
- `delivery_context` – for example `on_site_attraction`, `expo_or_tradeshow`, `museum_or_cultural_institution`.
- `channel_group` – commissioner type (for example `national_tourism_board`, `city_marketing`, `cultural_institution`, `commercial_operator`).
- `sector_tags` – tourism-related tags such as `nature_tourism`, `city_tourism`, `cultural_heritage`, `wine_and_gastronomy_tourism`.

Optional numerical fields (often null):

- `budget`, `production_costs`, `visitor_numbers`, `revenue`, `roi`  

These are only filled when reliable public information exists.

---

## 4. X (Twitter) feedback integration

For a subset of projects, the dataset includes structured references to X (Twitter) user posts.  
This is intended to capture public reaction and qualitative sentiment, not to build a complete social media archive.

Where available, entries may contain a `user_feedback` object:

- `x_posts` – an array of posts with:
  - `url` – direct link to the post.
  - `author_handle` – public X handle of the author.
  - `post_type` – for example `visitor_impression`, `press`, `creator_announcement`.
  - `summary` – very short paraphrase in English (not a full quote).
  - `engagement` – simple metrics (likes, reposts) at time of collection, if captured.

X posts are used only as references and paraphrased. This dataset does not intend to reproduce large amounts of verbatim social media content.

If no relevant X posts were found or considered, the `user_feedback` field is omitted for that project.

---

## 5. Data quality, TripAdvisor checks and verification

Data quality constraints:

- Sources – each project is backed by at least one public source; more critical cases use multiple independent sources.
- Dates – years are sometimes approximate when sources only mention relative time (“about ten years ago”, “since the 2010s”).
- Status – closed or historic projects are included when they illustrate important formats or strategies.

For fulldome attractions, flying theatres and similar visitor-facing venues, basic plausibility checks were also done against:

- TripAdvisor (existence of the attraction, basic visitor context, approximate operating period)  
- Other map and review platforms (for example Google Maps, where available)

These checks are used to confirm that projects actually operate or operated as public attractions and to understand their visitor framing, not to extract large-scale review data.

When using this dataset:

- treat numerical and financial values as indicative, not as audited figures  
- cross-check dates and status if your use case requires high precision (for example for investment decisions)  
- consider this dataset as a qualitative map, not as a complete census

---

## 6. Suggested uses

Examples of how you can work with this dataset:

- Strategy and consulting  
  Map which destinations use which immersive formats and in what contexts.
- Creative direction  
  Explore reference cases when designing new immersive destination experiences.
- Teaching and talks  
  Use the projects as case examples in lectures, workshops and conference presentations.
- Research  
  Analyse adoption patterns of immersive media in tourism, compare regions, formats or commissioner types.

If you publish work based on this dataset, a short citation and link back to the repository is appreciated.

---

## 7. Contributing

If you know of relevant projects that are missing, or if you find errors, you can:

- open an issue in the repository describing:
  - project name  
  - destination  
  - format  
  - one or two source links  
- or submit a pull request with:
  - a new project object added to `immersive-destination-marketing.json`,  
  - and a short note in the PR description explaining the change.

Please follow the existing field naming conventions and keep descriptions concise and neutral in tone.
