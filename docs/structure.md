# Jurassinkart Agent Team (outline)

## Repo bones
```text
agents/
  research/
  constraint/
  prompt_builder/
  reference_injector/
  image_critic/
  iteration/
  product_formatter/
  store_sync/
  content/

shared/
  schemas/
  species/
  prompt_parts/
  utils/

data/
  species_reference/
  reference_images/
  prompt_history/

workflows/
  generate_image_pipeline/
  product_launch_pipeline/
  content_pipeline/

outputs/
  prompts/
  critiques/
  product_packages/
  social_posts/

docs/
  agent_specs/
  migration_notes/

helpers/

scripts/

tests/
```

## Agent roster (one job each)

### Research Agent
**Input:** species name(s)

**Output:** structured species file(s) with anatomy + behavior details (JSON/YAML)

### Constraint Agent
**Input:** species file

**Output:** "allowed prompt boundaries" (hard locks: posture, anatomy, negative constraints)

### Prompt Builder
**Input:** species + constraints + narrative intent

**Output:** optimized base prompt (token-efficient)

### Reference Injector
**Input:** base prompt + references (skeletal / paleoart)

**Output:** prompt with reference blocks + weighted styles

### Image Critic
**Input:** generated image(s)

**Output:** critique JSON (fail reasons + severity + suggested fixes)

### Iteration Agent
**Input:** base prompt + critique JSON

**Output:** revised prompt (v2/v3...) + rationale

### Product Formatter
**Input:** final prompt/image metadata

**Output:** product package files (title, description, tags, ratios)

### Store Sync Agent
**Input:** product package

**Output:** synced product listings (web store / Printify / Etsy later)

### Content Agent
**Input:** new product + gallery

**Output:** growth content drafts (IG captions, Reddit post copy, tweet thread outline)

## Pipes (how they connect)

Research Agent → Constraint Agent → Prompt Builder → Reference Injector → (MJ render)
→ Image Critic → Iteration Agent (loop) → Product Formatter → Store Sync → Content Agent

## Migration plan

1) Create skeleton folders + docs (this file)
2) Move Research Agent code first; test
3) Move Constraint logic next; test
4) Move Prompt Builder; test
5) Only then wire the pipeline orchestration

## Notes
- Keep each agent package small: `/agents/<agent>/` should contain README + schema + tiny code
- Empty folders need a `.keep` or README so they exist in Git
