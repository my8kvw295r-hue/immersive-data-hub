## Visions_for_Immersive_Cities_NEOM_Beyond_2030

This dataset collects paraphrased, source-linked vision statements about AI-driven immersive cities, with NEOM as a focal example and a broader lens on urban futures beyond 2030. Each record encodes how cities are imagined to sense, interpret, and respond to individuals and groups through immersive media, multi-agent AI, and adaptive urban interfaces.

The goal is to make visionary urban thinking operational: visions become structured data that can be filtered, traced over time, and connected to concrete skills, roles, and concepts in the existing immersive skillgraph and knowledge graph.

### 1. Data model

Each entry in the dataset is a single, atomic vision statement with:

- A strictly ascending numeric ID:  
  `IVIC-000001`, `IVIC-000002`, … (no gaps, no reuse of IDs)
- A paraphrased statement that can be used directly in analysis or generation
- Full source metadata, including:
  - source_type (for example `research_paper`, `article`, `corporate_vision`, `interview`, `tweet`, `ms_article`)
  - source_title, source_url, source_publication_date
  - source_author and, where applicable, explicitly named quoted persons
- Temporal information:
  - vision_timeframe (what year or period the vision refers to, for example 2035)
  - entry_created_at (when the dataset entry was created or last updated)
- Analytical layers:
  - ai_layer (architectures, roles, data streams)
  - immersion_layer (modalities and interaction modes)
  - urban_system_function (for example governance, mobility, education, culture)
  - intent_type (prediction, speculation, marketing narrative, urban masterplan, research hypothesis, philosophical statement, product roadmap)
  - normative_evaluation (tone, opportunities, critical aspects)
  - storylines, semantic_anchors, and topic clusters for later graph and trend analysis
- Interoperability fields:
  - skillgraph_links (links to skills and roles from SkillTaxonomy_ImmersiveCreativeRoles)
  - knowledge_graph_links (links to concept nodes in martin-sambauer-knowledge-graph)

All paraphrased statements are designed to be directly usable as text snippets for exploration, analysis, and generative workflows.

### 2. Source policy

The dataset is strictly based on real, verifiable sources:

- No imaginary sources, no fabricated references, no invented quotes.
- No hallucinated content: every statement must be traceable to at least one concrete source.
- Scientific and scholarly sources are actively collected, labelled with `source_type = research_paper`, and treated as first-class citizens next to corporate visions, design studies, interviews, and articles.
- Author names and, where relevant, quoted persons are always recorded where the source provides them.

Duplicate records are not allowed:

- The same vision must not appear twice with different IDs.
- Before adding a new entry, annotators must check for duplicate or near-duplicate paraphrases and overlapping source URLs.

### 3. Interoperability with other datasets

This dataset is designed to work together with:

- SkillTaxonomy_ImmersiveCreativeRoles  
  Vision statements reference skills and roles needed to conceptualise, design, implement, and operate immersive cities.

- martin-sambauer-knowledge-graph  
  Vision statements link to concept nodes such as `immersive_city`, `multi_agent_ai`, `digital_twin`, `immersive_governance`, or `creative_director_for_immersive_media`.

These links enable graph-based exploration, such as:

- Which skills are repeatedly associated with high-impact urban AI visions?
- How do certain concept clusters (for example multi-agent AI plus immersive governance) evolve over time?

### 4. Collection and annotation overview

Source collection follows a three-layer sampling strategy:

- Canonical sources  
  Official NEOM and urban masterplan documents, research labs, scholarly publications, institutional reports.

- Emergent media and cultural tech  
  Architecture and design magazines, futurism blogs, think tanks, immersive design communities.

- Internal synthesis  
  Articles and texts by Martin Sambauer and derived internal syntheses. These are clearly marked with `source_type = ms_article` and are always distinguishable from external sources.

Every record is:

- Paraphrased into a clear, single statement
- Annotated with AI, immersion, and urban-system attributes
- Linked to skills, roles, and knowledge graph nodes where possible
- Tagged with intent_type, normative_evaluation, and storylines

For full procedures and instructions, see `methodology.md`.

### 5. Reuse and analysis ideas

Possible uses include:

- Tracking how specific urban AI storylines (such as the city as conversational partner) emerge and change over time.
- Identifying which skills and roles become central in high-impact visions of immersive cities.
- Building agent-based simulations and generative design tools that are grounded in documented, real-world visions rather than free-floating speculation.

Explore. repository folder · JSON · article with insights  
Licensing. CC BY 4.0 · © Martin Sambauer · martin-sambauer.com
