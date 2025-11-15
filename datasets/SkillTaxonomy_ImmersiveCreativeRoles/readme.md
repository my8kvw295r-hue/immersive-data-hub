# Skill Taxonomy for Immersive Creative Roles (Pilot v0.1.0)

This dataset defines an evidence-based skill taxonomy for immersive creative roles.  
In its current pilot version, it focuses on the role family "Creative Director for Immersive Media" and translates documented projects, productions and venues into structured, reusable skill descriptions.

The taxonomy is curated and maintained by Martin Sambauer (martin-sambauer.com).

## Ontology context

This dataset is part of the Immersive Datasets repository and follows the ontological framework described in `/ontology.md`.

Within that ontology, this taxonomy acts as the skill layer that connects:

- people and roles (Creative Directors for Immersive Media)  
- projects and destinations (immersive productions, destination marketing outputs)  
- immersive qualities and perceptual architectures (future datasets)

The taxonomy is designed to:

- make the work of a Creative Director for Immersive Media more transparent  
- provide a bridge between industry practice and education  
- support AI agents and tools that need structured, explainable competencies  
- enable cross-analysis with other datasets (creative directors, destinations, investors)

It builds directly on:

- `Creative Directors for Immersive Media` (cdim) – as the role backbone  
- `Immersive Destination Marketing` (dest_marketing) – as a source of concrete outputs and requirements  

These base datasets are referenced in `dataset_metadata.base_datasets` and in each skill’s `source_datasets` field.

## Dataset contents

The JSON file `SkillTaxonomy_ImmersiveCreativeRoles.json` contains two top-level keys:

- `dataset_metadata`  
  Core information about the taxonomy (id, name, version, dates, description, license, base datasets, methodology pointer and target audiences).

- `skills`  
  An array of individual skill units. Each skill is defined as a JSON object with fields such as:
  - `id` – stable identifier (e.g. `skill_00001`)  
  - `slug` – machine-friendly name  
  - `label` – human-readable skill name  
  - `skill_category` – high-level category (e.g. `narrative_and_concept`, `technical_and_tools`)  
  - `skill_subcategory` – more specific grouping (e.g. `immersive_story_structure`, `spatial_image_composition`)  
  - `skill_type` – type of competence (e.g. complex_competence)  
  - `description` – clear narrative description of the skill  
  - `cognitive_level` – typical level (e.g. intermediate, advanced, expert)  
  - `proficiency_levels` – intended scale for curriculum or HR use  
  - `associated_role_types` – mappings to immersive role families and subtypes  
  - `application_contexts` – media forms and environments where the skill is applied  
  - `derived_from_outputs` – references to concrete projects, venues or outputs that informed the skill  
  - `references` – bibliographic anchors and external sources  
  - `source_datasets` – links back to underlying datasets (e.g. cdim, dest_marketing)  
  - `overlaps_with_skills`, `is_component_of`, `is_prerequisite_for` – semantic relations within the taxonomy  
  - `tags` – additional keywords for search and clustering  
  - `notes`, `created`, `last_updated` – meta fields

## Key results from pilot v0.1.0

From the current pilot version (176 skills), several structural patterns are already visible:

1. A focused but rich skill set for Creative Directors  
   All 176 skills are currently mapped to the role family `creative_director_for_immersive_media` via `associated_role_types`.  
   This confirms the taxonomy’s initial intention: to describe the full breadth of competencies needed for this role rather than a generic media skills catalogue.

2. Seven main skill categories with a strong narrative and conceptual core  
   The taxonomy uses seven `skill_category` values in this pilot:

   - narrative_and_concept (74 skills)  
   - technical_and_tools (44 skills)  
   - production_and_leadership (23 skills)  
   - production_and_management (18 skills)  
   - research_and_evaluation (11 skills)  
   - interaction_design (4 skills)  
   - audio_and_sound (2 skills)

   This distribution emphasises that immersive creative direction is, first of all, a narrative and conceptual practice that is deeply intertwined with technology, production and evaluation, rather than a purely technical function.

3. Fine-grained substructure for curricula and role design  
   Across categories, the taxonomy currently uses 150+ `skill_subcategory` combinations.  
   These range from “immersive_story_structure”, “spatial_image_composition” and “expanded_cinema_and_multi_projection” to “ar_navigation”, “haptic_interaction” and “procedural_audio”.

   This level of granularity makes it possible to:

   - derive modular curricula for immersive media programmes  
   - plan team compositions for specific projects (e.g. fulldome vs XR vs architectural media)  
   - identify gaps in existing training offers and internal skill sets.

4. Advanced cognitive level with a clear progression model  
   The `cognitive_level` field is dominated by higher-order levels:

   - 126 skills are marked as `advanced`  
   - 25 as `intermediate`  
   - 25 as `expert`

   Most skills share a typical progression in `proficiency_levels`:

   - `basic_awareness` → `operational` → `expert` (122 skills)  
   - variants including `advanced` or `master` for a smaller subset

   This reflects the reality that immersive creative direction is a senior practice: entry-level familiarity is possible, but true competence requires operational and expert experience.

5. Evidence-based links to real projects and destinations  
   Through `derived_from_outputs` and `source_datasets`, each skill can be traced back to:

   - documented creative directors and their roles (cdim)  
   - real destination marketing outputs and immersive projects (dest_marketing)

   This ensures that skills are not invented in the abstract but grounded in actual practice across fulldome, XR, installations and destination storytelling.

6. Ready for future stacking with destinations, investors and immersive qualities  
   The relational fields (`associated_role_types`, `source_datasets`, `is_prerequisite_for`, `overlaps_with_skills`) are designed so that:

   - skills can be connected to specific types of destinations and projects  
   - future investor datasets can be linked to required skill clusters  
   - a future dataset on immersive qualities can be mapped to the competences needed to realise specific perceptual effects

   In other words, this taxonomy is not an isolated list but a structural layer in a larger graph of immersive ecosystems.

## Field overview

A non-exhaustive overview of key fields in each skill object:

- Identity and semantics  
  - `id`, `slug`, `label`  
  - `skill_category`, `skill_subcategory`  
  - `skill_type`  
  - `description`  

- Depth and level  
  - `cognitive_level`  
  - `proficiency_levels`

- Role mapping  
  - `associated_role_types` (role family, subtype, source dataset)

- Application and context  
  - `application_contexts`  
  - `derived_from_outputs`  

- Evidence and references  
  - `references` (title, author, year, URL where applicable)  
  - `source_datasets` (ids and names of base datasets)

- Relations within the taxonomy  
  - `overlaps_with_skills`  
  - `is_component_of`  
  - `is_prerequisite_for`

- Meta  
  - `tags`, `notes`  
  - `created`, `last_updated`

For detailed methodology, see the dataset-specific methodology file referenced in `dataset_metadata.methodology.document`.

## Methodology (summary)

A full description is provided in `methodology.md`. In summary, the taxonomy was created through:

1. Evidence collection  
   Skills were derived from documented immersive projects, destination marketing outputs, venue programmes, festival line-ups and role descriptions, with a focus on Creative Directors for Immersive Media.

2. Cross-dataset triangulation  
   The Creative Directors dataset (`cdim`) and the Immersive Destination Marketing dataset (`dest_marketing`) were used to identify recurring tasks, responsibilities and capabilities that appear across projects and regions.

3. Skill formulation  
   Each identified competence was rewritten into a clear, teachable skill unit with:

   - description  
   - application contexts  
   - typical cognitive level and proficiency levels  
   - references and examples

4. Semantic structuring  
   Skills were classified into categories and subcategories, and relational fields were added to express prerequisites, overlaps and composite competencies.

5. Validation and iteration  
   Inconsistent or redundant skills were merged, and gaps were identified for future iterations. The taxonomy is designed to evolve as new immersive practices and roles emerge.

## Limitations and planned extensions

- Role scope  
  The current pilot is focused on the Creative Director for Immersive Media role family. Future versions may:

  - add other immersive roles (e.g. immersive technical director, experience designer, immersive producer)  
  - introduce mappings between roles (shared and role-specific skills)

- Regional and institutional validation  
  The taxonomy is grounded in a broad international practice but has not yet been systematically validated with multiple universities, training programmes and industry partners.

- Integration with external frameworks  
  Future work may align the taxonomy with widely used qualification or competency frameworks to support formal curricula and funding applications.

Planned extensions include:

- adding more skills where new practice emerges (e.g. AI-augmented workflows, large-scale XR stages, urban media architecture)  
- refining relations between skills and immersive qualities  
- testing the taxonomy in concrete curriculum and workshop design.

## Suggested use cases

Typical uses of this dataset include:

- curriculum design for film, media and design schools focusing on immersive media  
- internal skill audits and team planning in studios, museums, domes and agencies  
- mapping project requirements to concrete competencies for immersive productions  
- AI-based matching between projects, people and training resources  
- research into how immersive creative roles evolve across media, regions and sectors  

Because every skill is documented with descriptions, contexts and references, the taxonomy can be used directly in teaching, project planning and role definition.

## Citation

If you use this dataset, please include an attribution such as:

Skill Taxonomy for Immersive Creative Roles (Pilot v0.1.0), curated by Martin Sambauer (martin-sambauer.com). Part of the Immersive Datasets repository. Licensed under CC BY 4.0.
