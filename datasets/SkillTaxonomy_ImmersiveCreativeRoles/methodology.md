
## Purpose

This document explains how the “Skill Taxonomy for Immersive Creative Roles” is constructed and how it should be extended.

The taxonomy aims to:

- describe the skills of Creative Directors for Immersive Media and related roles
- ground these skills in real outputs and practice
- make them usable for curricula, policy and self-directed learning
- keep the dataset compatible with AI agents that work directly on the raw JSON

## Evidence integrity principle (important)

All evidence used in this taxonomy **must be real, verifiable and properly sourced**.

- No invented sources
- No hallucinated projects or people
- Every reference must be checked for existence
- Each evidence entry must be linked to a real URL, publication, dataset or work

This is mandatory for both:
- Primary evidence (base datasets)
- Secondary evidence (external enrichment)


## No-duplication rule (unique skills only)

Before a new skill is added to the taxonomy, existing skills MUST be checked to avoid duplicates.

- Each skill must be unique in function, scope and meaning.
- If a candidate skill substantially overlaps with an existing one, the existing skill should be enriched (more evidence, clearer description, additional relationships) instead of creating a new entry.
- New skills must either:
  - cover a genuinely new competence, or
  - clearly narrow/extend the scope of an existing competence with an explicit distinction in the description.

This rule applies to both base-dataset-derived skills and external-enrichment skills. Uncontrolled duplication would weaken curriculum design, policy analysis and AI usage of the taxonomy.

## Data sources

### Base datasets (primary layer)

The primary evidence comes from two datasets:

1. `cdim` – Creative Directors for Immersive Media  
2. `dest_marketing` – Destination Marketing Immersive Outputs

In this layer, each skill is derived from analysing real entries in these datasets.

### External enrichment layer (secondary layer)

A second evidence layer enriches and generalises the taxonomy with **real, verified** external sources:

- educational frameworks  
- job and role descriptions  
- interviews and practice essays  
- reports and research documents  

Enrichment is allowed **only if backed by real and verifiable sources**.

## Skill construction process

### Step 0 – Define scope  
### Step 1 – Extract primary evidence  
### Step 2 – Web research (mandatory, with real checked sources)  
### Step 3 – Narrative formulation  
### Step 4 – Define relationships  
### Step 5 – Role types and contexts  
### Step 6 – Versioning  

## Evidence layers inside the JSON

Skills may include an optional `"evidence_layer"` field:

- `"base_dataset"`
- `"external_enrichment"`
- `"hybrid"`

Every layer must contain **real, verifiable sources**.

## Update policy

- Skills are never deleted
- New skills link forward to older ones
- All sources must be real, checked and documented

## Interoperability

The taxonomy supports:

- curriculum designers
- policy makers
- practitioners
- self-directed learners
- AI agents

Evidence integrity ensures reliability across all these domains.
