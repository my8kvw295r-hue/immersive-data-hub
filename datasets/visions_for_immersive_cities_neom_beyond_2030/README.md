## Visions_for_Immersive_Cities_NEOM_Beyond_2030

This dataset collects paraphrased, source-linked vision statements about AI-driven immersive cities, with NEOM as a focal example and a broader lens on urban futures beyond 2030. Each record encodes how cities are imagined to sense, interpret, and respond to individuals and groups through immersive media, multi-agent AI, and adaptive urban interfaces.

The entire dataset is English-only.  
All paraphrased statements, metadata fields, tags, normative evaluations, and analytical annotations are written in English, even if the underlying sources are in other languages.

The goal is to make visionary urban thinking operational: visions become structured data that can be filtered, traced over time, and connected to concrete skills, roles, and concepts in the existing immersive skillgraph and knowledge graph.

### 1. Data model

Each entry in the dataset is a single, atomic vision statement with:

- project_name  
  A concise label for the project, platform or vision (e.g. "THE LINE, NEOM", "MACeIP platform").
- A strictly ascending numeric ID:  
  `IVIC-000001`, `IVIC-000002`, ... (no gaps, no reuse of IDs).
- A paraphrased statement that can be used directly in analysis or generation.
- Full source metadata, including:
  - source_type (for example `research_paper`, `urban_masterplan`, `conceptual_vision`, `critical_essay`, `ms_article`)
  - source_title, source_url, source_publication_date
  - source_author and, where applicable, explicitly named quoted persons.
- Provenance fields:
  - originators (who initiated or led the project or vision)
  - institutions (companies, universities, labs, funds associated with it)
  - related_research (papers, books, or whitepapers that investigate or formalise the vision)
- Temporal information:
  - vision_timeframe (what year or period the vision refers to, for example 2035)
  - entry_created_at (when the dataset entry was created or last updated)
- Analytical layers:
  - ai_layer (architectures, roles, data streams, multi-agent structure, human-in-the-loop)
  - immersion_layer (modalities, interaction modes, sensing/actuation, XR distribution)
  - urban_system_function (for example governance, mobility, education, culture)
  - intent_type (prediction, speculation, marketing narrative, urban masterplan, research hypothesis, philosophical statement, product roadmap, technical platform, research synthesis, conceptual vision, critical reflection)
  - normative_evaluation:
    - tone (a taxonomy of utopian, dystopian, critical, balanced, neutral)
    - opportunity_aspects and critical_aspects
  - storylines, semantic_anchors, and topic_clusters for later graph and trend analysis.
- Interoperability fields:
  - skillgraph_links (links to skills and roles from SkillTaxonomy_ImmersiveCreativeRoles)
  - knowledge_graph_links (links to concept nodes in martin-sambauer-knowledge-graph)

All paraphrased statements are designed to be directly usable as text snippets for exploration, analysis, and generative workflows.

### 2. Source policy

The dataset is strictly based on real, verifiable sources:

- No imaginary sources, no fabricated references, no invented quotes.
- No hallucinated content: every statement must be traceable to at least one concrete source.
- Scientific and scholarly sources are actively collected, labelled with `source_type = research_paper`, and treated as first-class citizens next to corporate visions, technical platforms, design studies, interviews, and essays.
- Author names and, where relevant, quoted persons are always recorded where the source provides them.
- Institutions, labs and universities are recorded where they are central to the project or research.

Duplicate records are not allowed:

- The same vision must not appear twice with different IDs.
- Before adding a new entry, annotators must check for duplicate or near-duplicate paraphrases and overlapping source URLs.

### 3. Utopia, dystopia, and critique: normative taxonomy

To separate visionary promise, dystopian risk, and analytical critique, each entry includes a `normative_evaluation` with:

- tone  
  - `utopian`: the vision is framed mainly in terms of promise, opportunity and positive transformation.  
  - `dystopian`: the vision is framed mainly in terms of risk, harm, surveillance, control or loss of rights.  
  - `critical`: the source is primarily an analytical critique or warning that focuses on problems and risks, without fully constructing a dystopian world.  
  - `balanced`: the source explicitly combines both promise and risk, often weighing benefits and harms side by side.  
  - `neutral`: the source is predominantly descriptive or technical, with little explicit normative framing.

- opportunity_aspects  
  Concrete positive aspects, for example "time-saving", "environmental management", "better city planning".

- critical_aspects  
  Concrete risks or problems, for example "loss of privacy", "centralised data power", "new forms of exclusion".

This taxonomy allows you to query and analyse:

- pure utopian NEOM statements,  
- dystopian framings of surveillance cities,  
- critical essays and warnings,  
- or balanced academic reviews of AI in cities.

### 4. Interoperability with other datasets

This dataset is designed to work together with:

- SkillTaxonomy_ImmersiveCreativeRoles  
  Vision statements reference skills and roles needed to conceptualise, design, implement, and operate immersive cities.

- martin-sambauer-knowledge-graph  
  Vision statements link to concept nodes such as `immersive_city`, `multi_agent_ai`, `digital_twin`, `immersive_governance`, or `creative_director_for_immersive_media`.

These links enable graph-based exploration, such as:

- Which skills are repeatedly associated with high-impact visions of immersive cities?
- How do certain concept clusters (for example multi-agent AI plus immersive governance) evolve over time?
- How do utopian and dystopian framings cluster around specific concepts and skills?

### 5. Collection and annotation overview

Source collection follows a three-layer sampling strategy:

- Canonical sources  
  Official NEOM and urban masterplan documents, research labs, scholarly publications, institutional reports.

- Emergent media and cultural tech  
  Architecture and design magazines, futurism blogs, think tanks, immersive design communities.

- Internal synthesis  
  Articles and texts by Martin Sambauer and derived internal syntheses. These are clearly marked with `source_type = ms_article` and are always distinguishable from external sources.

Every record is:

- Paraphrased into a clear, single English statement,
- Annotated with AI, immersion, urban-system attributes and normative tone,
- Linked to skills, roles, and knowledge graph nodes where possible,
- Enriched with originators, institutions and related research.

For full procedures and instructions, see `methodology.md`.

### 6. Reuse and analysis ideas

Possible uses include:

- Tracking how specific urban AI storylines (such as the city as conversational partner) emerge and change over time.
- Identifying which skills and roles become central in utopian versus dystopian visions of immersive cities.
- Comparing academic, corporate and critical perspectives on NEOM and other city-scale AI projects.
- Building agent-based simulations and generative design tools that are grounded in documented, real-world visions rather than free-floating speculation.

Explore. repository folder · JSON · article with insights  
Licensing. CC BY 4.0 · © Martin Sambauer · martin-sambauer.com
