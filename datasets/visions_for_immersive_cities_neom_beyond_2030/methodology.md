## Visions_for_Immersive_Cities_NEOM_Beyond_2030 – Methodology

This document describes how the dataset is constructed, which sources are used, how entries are paraphrased and annotated, and which quality rules apply.

### 1. Scope and unit of analysis

The dataset captures visions of immersive cities in which AI, multi-agent systems, and immersive media infrastructures orchestrate urban life. NEOM serves as an important focal example, but the scope explicitly extends to other cities and generic future urban scenarios beyond 2030.

The unit of analysis is a single atomic vision statement:

- One entry corresponds to one coherent idea about how an immersive city functions, feels, or is governed.
- Long sources may yield several entries if they contain multiple distinct vision statements.

Each entry is stored as one object in the dataset JSON file.

### 2. ID policy

Each entry receives a numeric, strictly ascending ID:

- Format: `IVIC-000001`
- Prefix: `IVIC`
- Numeric part: zero-padded integer starting from 1
- No gaps, no reuse of IDs, no reordering of existing IDs

New entries are always appended with the next free number.

### 3. Source collection strategy

Source collection follows a three-layer strategy:

3.1 Canonical sources

- Urban masterplans and official NEOM documents
- Research papers and scholarly publications in urban studies, AI, human–computer interaction, XR, and related fields
- Institutional reports (for example labs, research centres, think tanks, universities)

These are labelled with:

- `source_type = research_paper` for scholarly work (journals, conferences, arxiv where appropriate)
- `source_type = corporate_vision` or `urban_masterplan` for official planning documents

3.2 Emergent media and cultural tech

- Architecture and design magazines
- Urban futurism blogs and think tank essays
- Immersive design communities and XR-oriented publications

These are typically labelled as `article` or `other`, depending on the outlet.

3.3 Internal synthesis

- Articles by Martin Sambauer and related internal texts are included as sources in their own right.
- They are labelled with `source_type = ms_article`, and `ms_origin.is_martin_article = true`.

This makes internal reasoning and synthesis transparent and distinguishable from external sources.

### 4. Strict AI and source rules

This dataset is designed to be grounded, auditable, and reproducible. The following rules apply to all annotators, including AI-based agents:

- Only real, verifiable sources are allowed.
- No fabricated sources, no made-up titles, no imaginary authors, no invented URLs.
- No hallucinations: every paraphrased statement must be traceable to at least one concrete source that actually exists and can be accessed.
- No fabricated quotes or paraphrases of people who never said or wrote the underlying idea.
- Before creating a new record, annotators must:
  - Check whether the source already exists in the dataset.
  - Check whether a similar paraphrased statement already exists for the same source.

Duplicates are strictly forbidden:

- The same vision must not be encoded twice under different IDs.
- Near-identical paraphrases from the same source should be merged into one entry where possible.

If an AI agent is used for pre-annotation:

- It must be instructed to work only from the provided, verified source texts (for example via context injection).
- It must never invent new sources or statement content beyond what is supported by the text.
- Any low-confidence cases must be flagged for human review.

### 5. Recording authors and quoted persons

For each entry, the dataset aims to record authorship and attribution as precisely as possible:

- `source_author` records the primary author(s) of the document where available.
- If the vision is expressed by a quoted person (for example in an interview or article), this person should be recorded in `quoted_persons`.
- When a vision is clearly attributed to a specific researcher, architect, or public figure, annotators should ensure that person appears in the metadata.

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

### 7. Temporal and impact fields

Each entry separates multiple time and impact dimensions:

- `source_publication_date`  
  When the source was originally published.

- `entry_created_at`  
  When the dataset entry was created or last updated.

- `vision_timeframe`  
  The year or range the vision refers to (for example 2030, 2035–2040).

Optionally, additional fields can be used:

- technological_readiness_estimate (0–1)
- adoption_timeframe_low / adoption_timeframe_high (years)
- near_term_impact, long_term_impact, system_transform_potential (0–1)

These fields capture how bold or realistic a vision is in the context of technology and society.

### 8. Analytical layers

8.1 AI layer

The `ai_layer` object describes how AI appears in the vision:

- ai_architecture  
  Examples: multi_agent_system, digital_twin_city, centralised_orchestrator, edge_ai, transformer_swarm

- ai_roles  
  Examples: personal_companion_agent, urban_orchestration_agent, governance_assistant, mobility_optimizer

- data_streams  
  Examples: sensor_network, mobility_data, behavioral_analytics, social_graph, biosignals

- coordination_protocols  
  Optional description of how different agents or components coordinate, for example via blackboard systems or swarm logic.

8.2 Immersion layer

The `immersion_layer` object describes how immersive media manifests:

- modalities  
  Examples: fulldome, led_dome, ar, vr, mixed_reality, ambient_media_architecture, projection_mapping

- interaction_modes  
  Examples: group_co-experience, personalised_overlay, event_driven_storyworld, always_on_ambient_layer

- sensory_richness  
  Coarse rating of how many senses and channels the vision involves (low, medium, high).

8.3 Urban system function

The `urban_system_function` field connects the vision to components of the urban system, for example:

- governance, mobility, education, health, energy, culture, security, environment, commerce, public_space, identity, other

8.4 Intent and evaluation

- intent_type  
  prediction, speculation, marketing_narrative, urban_masterplan, research_hypothesis, philosophical_statement, product_roadmap, other

- normative_evaluation  
  tone (utopian, dystopian, neutral, mixed), plus lists of opportunity_aspects and critical_aspects.

### 9. Interoperability with skills, roles, and concepts

Each entry can link to:

- Skills and roles from SkillTaxonomy_ImmersiveCreativeRoles via `skillgraph_links.related_skills` and `skillgraph_links.related_roles`.
- Concept nodes from martin-sambauer-knowledge-graph via `knowledge_graph_links.concept_nodes`.

These links should be assigned whenever:

- The vision clearly implies that a certain skill is required to implement or operate the described system.
- The vision clearly fits into an existing concept category (for example immersive_governance, city_as_computer, ambient_intelligence).

A separate edge file can record relationships such as:

- requires, enables, depends_on, contradicts, extends

### 10. Storylines, clusters, and semantic anchors

To support longitudinal and qualitative analysis:

- Each entry can be assigned to one or more storylines, such as:
  - city_as_conversational_partner
  - immersive_governance
  - multi_agent_mobility
  - ambient_emotion_lightfields
  - bio_sensing_architecture

- Semantic anchors can be used to stabilise embeddings and agent behaviour, for example:
  - city_as_computer
  - ambient_intelligence
  - planetary_scale_computation
  - adaptive_narrative_environments

Topic modelling or clustering can be run periodically to group entries into emergent clusters; cluster IDs can then be stored with each entry.

### 11. Quality control

Quality control operates on several levels:

- Source validation  
  Check that every source exists, is reachable, and is correctly typed.

- Duplication checks  
  Before saving a new entry, compare:
  - source_url and source_identifier
  - paraphrased_statement similarity with existing entries

- Consistency checks  
  Ensure that required fields (ID, paraphrased_statement, source, vision_timeframe, entry_created_at) are present and syntactically valid.

- Review  
  Low-confidence annotations (for example borderline paraphrases or ambiguous intent_type) should be flagged for human review and clearly marked as such.

By following these rules, the dataset can grow into a reliable, extensible foundation for analysing and generating visions of immersive cities, grounded in real sources and tightly integrated with existing skill and knowledge graphs.
