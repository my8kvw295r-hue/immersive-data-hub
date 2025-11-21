## Visions_for_Immersive_Cities_NEOM_Beyond_2030 – Methodology

This document describes how the dataset is constructed, which sources are used, how entries are paraphrased and annotated, and which quality rules apply.

The dataset is entirely English-only.  
All paraphrased statements, metadata fields, tags, normative evaluations, and analytical annotations are written in English, even when the underlying sources are in other languages.

### 1. Scope and unit of analysis

The dataset captures visions of immersive cities in which AI, multi-agent systems, and immersive media infrastructures orchestrate urban life. NEOM serves as an important focal example, but the scope explicitly extends to other cities and generic future urban scenarios beyond 2030.

The unit of analysis is a single atomic vision statement:

- One entry corresponds to one coherent idea about how an immersive city functions, feels, or is governed.
- Long sources may yield several entries if they contain multiple distinct vision statements.

Each entry is stored as one object in the main dataset JSON file.

### 2. ID policy

Each entry receives a numeric, strictly ascending ID:

- Format: `IVIC-000001`
- Prefix: `IVIC`
- Numeric part: zero-padded integer starting from 1
- No gaps, no reuse of IDs, no reordering of existing IDs

New entries are always appended with the next free number.

### 3. Source collection strategy

Source collection follows a three-layer strategy:

#### 3.1 Canonical sources

- Urban masterplans and official NEOM documents.
- Research papers and scholarly publications in urban studies, AI, human–computer interaction, XR and related fields.
- Institutional reports (for example labs, research centres, think tanks, universities).

These are labelled with:

- `source_type = research_paper` for scholarly work (journals, conferences, arxiv where appropriate).
- `source_type = corporate_vision` or `urban_masterplan` for official planning documents.
- `source_type = technical_platform` for platform or architecture descriptions.

#### 3.2 Emergent media and cultural tech

- Architecture and design magazines.
- Urban futurism blogs and think tank essays.
- Immersive design communities and XR-oriented publications.

These are typically labelled as `article`, `conceptual_vision`, `critical_essay`, or `other`, depending on the outlet and content.

#### 3.3 Internal synthesis

- Articles by Martin Sambauer and related internal texts are included as sources in their own right.
- They are labelled with `source_type = ms_article`, and `ms_origin.is_martin_article = true`.

This makes internal reasoning and synthesis transparent and clearly distinguishable from external sources.

### 4. Strict AI and source rules

This dataset is designed to be grounded, auditable, and reproducible. The following rules apply to all annotators, including AI-based agents:

- Only real, verifiable sources are allowed.
- No fabricated sources, no made-up titles, no imaginary authors, no invented URLs.
- No hallucinations: every paraphrased statement must be traceable to at least one concrete source that actually exists and can be accessed.
- No fabricated quotes or paraphrases of people who never said or wrote the underlying idea.
- All source metadata, originators, institutions and related_research entries must correspond to real entities and publications and must be consistent with the underlying sources.

Before creating a new record, annotators must:

- Check whether the source already exists in the dataset.
- Check whether a similar paraphrased statement already exists for the same source.

Duplicates are strictly forbidden:

- The same vision must not be encoded twice under different IDs.
- Near-identical paraphrases from the same source should be merged into one entry where possible.

If an AI agent is used for pre-annotation:

- It must be instructed to work only from the provided, verified source texts (for example via context injection).
- It must never invent new sources or statement content beyond what is supported by the text.
- Any low-confidence cases must be flagged for human review.

### 5. Recording authors, originators, and institutions

For each entry, the dataset aims to record authorship, origin and institutional context as precisely as possible:

- `source_author` records the primary author(s) of the document where available.
- `quoted_persons` records individuals explicitly quoted or named as originators of the vision in the source.
- `originators` records key people associated with inventing, initiating or leading the project or vision (for example founders, lead authors, principal investigators, chief technologists).
- `institutions` records associated companies, universities, labs, funds or departments, including institution type and country.
- `related_research` records specific research works (journal articles, conference papers, books, whitepapers, essays) that conceptualise, formalise or critically examine the vision.

If the source does not declare any author, `source_author` can be omitted or replaced by the organisation name in `source_organization`.

### 6. Paraphrasing protocol

Each vision statement is paraphrased according to the following rules:

- The paraphrased statement must faithfully represent the meaning and intent of the source.
- It should be written as a clear, complete sentence that can stand on its own.
- It must not be a verbatim quote beyond very short, legally safe fragments.
- It should abstract away local details that are not central to the vision, while preserving key mechanisms (for example “the city continuously senses movement and emotion and adapts its media surfaces in real time”).

Paraphrased statements must be:

- Specific enough to be useful in analysis and generation.
- Neutral in tone; evaluative judgements are moved into `normative_evaluation`.

All paraphrasing is done in English, even when the original source is in another language.

### 7. Temporal and impact fields

Each entry separates multiple time and impact dimensions:

- `source_publication_date`  
  When the source was originally published.

- `entry_created_at`  
  When the dataset entry was created or last updated.

- `vision_timeframe`  
  The year or range the vision refers to (for example 2030, 2035–2040).

Optional impact fields:

- `technological_readiness_estimate` (0–1).
- `adoption_timeframe_low` / `adoption_timeframe_high` (years).
- `near_term_impact`, `long_term_impact`, `system_transform_potential` (0–1).

These fields capture how bold or realistic a vision is in the context of technology and society.

### 8. Analytical layers

#### 8.1 AI layer

The `ai_layer` object describes how AI appears in the vision:

- `ai_layers_present`  
  High-level functions such as perception, prediction, decision_support, personalisation.

- `ai_roles`  
  Examples: personal_companion_agent, urban_orchestration_agent, governance_assistant, mobility_optimizer.

- `data_streams`  
  Examples: mobility, environmental_sensors, biometric_data, social_graph, infrastructure_usage.

- `ai_architecture`  
  Examples: multi_agent_system, digital_twin_city, edge_cloud_hybrid, city_operating_system.

- `multi_agent_structure`  
  Optional description of how agents are organised (for example service-specific modules, federated city services).

- `human_in_the_loop`  
  Description of how humans remain in control or approve decisions.

#### 8.2 Immersion layer

The `immersion_layer` object describes how immersive media manifests:

- `immersive_modalities`  
  Examples: fulldome, led_dome, ar, vr, ambient_intelligence, projection_mapping.

- `interaction_modes`  
  Examples: group_co-experience, personalised_overlay, implicit_contextual, voice, avatar_based.

- `sensing_actuation`  
  Examples: ubiquitous_sensors, public_displays, facial_recognition, environmental_controls.

- `xr_distribution`  
  Examples: mixed_reality_metaverse, headsets, interactive_hubs.

#### 8.3 Urban system function

The `urban_system_function` field maps the vision to components of the urban system, for example:

- governance, mobility, education, health, energy, culture, security, environment, commerce, public_space, housing, asset_management, planning, public_services, civic_participation, economy, other.

#### 8.4 Intent type

The `intent_type` field encodes the intent of the source:

- prediction, speculation, marketing_narrative, urban_masterplan, research_hypothesis, philosophical_statement, product_roadmap, technical_platform, research_synthesis, conceptual_vision, critical_reflection, other.

### 9. Utopia, dystopia, and critique

The `normative_evaluation` object encodes the normative framing of the vision:

- `tone` (taxonomy of utopia, dystopia, and critique):
  - `utopian`: the vision emphasises promise, hope, efficiency or transformation, with limited explicit concern for risks.
  - `dystopian`: the vision emphasises harms, control, surveillance, loss of rights or negative systemic outcomes.
  - `critical`: the source is primarily an analytical critique or warning, focusing on risks without fully building a dystopian future scenario.
  - `balanced`: the source explicitly places promises and risks side by side and discusses both in a structured way.
  - `neutral`: the source is mainly descriptive or technical, without strong normative language.

- `opportunity_aspects`  
  A list of concrete positive aspects highlighted (for example time-saving, better city planning, environmental management, improved health).

- `critical_aspects`  
  A list of concrete negative aspects highlighted (for example surveillance, loss of privacy, algorithmic bias, centralised data power).

Annotators should:

- Use `utopian` for strongly promotional NEOM and corporate-vision language.
- Use `dystopian` for texts that primarily portray immersive AI cities as risks or as dark futures.
- Use `critical` for essays and papers that focus on critique and warnings, especially from academic or architectural perspectives.
- Use `balanced` for reviews and reports that explicitly discuss both benefits and drawbacks.
- Use `neutral` for technical descriptions with minimal explicit evaluation.

### 10. Interoperability with skills, roles, and concepts

Each entry can link to:

- Skills and roles from SkillTaxonomy_ImmersiveCreativeRoles via `skillgraph_links.related_skills` and `skillgraph_links.related_roles`.
- Concept nodes from martin-sambauer-knowledge-graph via `knowledge_graph_links.concept_nodes`.

These links should be assigned whenever:

- The vision clearly implies that a certain skill is required to implement or operate the described system.
- The vision clearly fits into an existing concept category (for example immersive_governance, city_as_computer, ambient_intelligence).

A separate edge file can record relationships such as:

- requires, enables, depends_on, contradicts, extends.

### 11. Storylines, clusters, and semantic anchors

To support longitudinal and qualitative analysis:

- Each entry can be assigned to one or more storylines, such as:
  - city_as_conversational_partner
  - immersive_governance
  - multi_agent_mobility
  - ambient_emotion_lightfields
  - bio_sensing_architecture.

- Semantic anchors can be used to stabilise embeddings and agent behaviour, for example:
  - city_as_computer
  - ambient_intelligence
  - planetary_scale_computation
  - adaptive_narrative_environments.

Topic modelling or clustering can be run periodically to group entries into emergent clusters; cluster IDs can then be stored with each entry in `topic_clusters`.

### 12. Quality control

Quality control operates on several levels:

- Source validation  
  Check that every source exists, is reachable, and is correctly typed.

- Provenance validation  
  Check that originators, institutions and related_research entries match the underlying sources and do not introduce imaginary entities.

- Duplication checks  
  Before saving a new entry, compare:
  - source_url and source_identifier,
  - paraphrased_statement similarity with existing entries.

- Consistency checks  
  Ensure that required fields (ID, project_name, paraphrased_statement, source, vision_timeframe, entry_created_at) are present and syntactically valid.

- Review  
  Low-confidence annotations (for example borderline paraphrases, unclear tone, or ambiguous intent_type) should be flagged for human review and clearly marked as such.

By following these rules, the dataset can grow into a reliable, extensible foundation for analysing and generating visions of immersive cities, grounded in real sources and tightly integrated with existing skill and knowledge graphs.
