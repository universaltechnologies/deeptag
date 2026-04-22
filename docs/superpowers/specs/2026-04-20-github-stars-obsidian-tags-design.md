# GitHub Stars Obsidian Tags Design

## Goal

Transform GitHub starred repos into Obsidian notes with semantic flat tags for knowledge graph association.

## Tag Philosophy

- Tags are **flat** (one per line, no slash nesting)
- The taxonomy tree defines semantic relationships, not nesting
- Tags from the tree are output as individual nodes: `pbr` implies relation to `shader` implies relation to `graphic`
- Cross-cutting tags (awesome, template, library, etc.) are orthogonal to domain tags
- Hierarchy priority: graphic > coding > tools; match most specific applicable tag(s)

## Tag Matching Rules

1. Each repo gets tags from the taxonomy based on README + description + topics + language
2. Tags are flat: `graphic`, `shader`, `pbr` — not `graphic/shader/pbr`
3. Cross-cutting type tags (awesome, template, etc.) are added independently
4. Repos that cannot be classified are tagged with `misc` + recorded for review
5. Repos where README cannot be extracted: record and skip

## Taxonomy (Tag Dictionary)

### graphic

```
shader
  pbr
  toon
  hlsl
  glsl
  compute_shader
rendering
  rasterization
  ray_tracing
  path_tracing
  gi
  volume
  post_processing
rhi
  opengl
  vulkan
  directx
  metal
  webgpu
mesh
animation
skeletal
modeling
procedural
physics
texture
  vtf
  atlas
math
tools
  shader (tool)
  texture (tool)
  pipeline
  profiler
  debug
  color
  modeling (tool)
  capture
misc
```

### coding

```
language
  cpp
    raii
    template
    stl
  csharp
  rust
  python
  typescript
  javascript
  c
  go
  java
  lua
  kotlin
ai
  llm
  agent
  ml
  cv
  nlp
  diffusion
  rag
  voice
  mcp
  prompt
  memory
  context
  tokens
  skills
  harness
  spec
engine
  unity
  unreal
  godot
  custom
game
  ecs
  gameplay
  networking
web
  frontend
  backend
  api
algorithm
performance
  memory
  concurrency
  simd
architecture
practice
hardware
reverse
mobile
platform
tools
  editor
  cli
  git
  debug
  profiler
  ci
  test
  lint
  build
  package
  scaffold
misc
```

### tools

```
office
compute
productivity
browser
network
security
misc
```

### Cross-cutting (Type Tags)

```
awesome
template
tutorial
library
tool
service
plugin
```

## File Structure

```
obsidian_github/
├── stars/
│   ├── notes/                    # Tag notes (flat, no sub-folders)
│   │   └── owner_repo.md
│   └── readme/                   # Original README files
│       └── owner_repo.md
├── starred_repos.json            # Source data
├── untagged.json                 # Repos that couldn't be tagged
├── misc_tagged.json              # Repos tagged with misc
└── ambiguous.json                # Repos needing manual review
```

## Note Format

`stars/notes/owner_repo.md`:

```markdown
---
title: "owner/repo"
repo: https://github.com/owner/repo
homepage: "..."
language: C++
stars: 1234
topics: [topic1, topic2]
starred_at: "2024-01-01T00:00:00Z"
tags:
  - graphic
  - shader
  - pbr
  - awesome
---

# owner/repo

> Description text

![[readme/owner_repo]]
```

## Processing Pipeline

### Phase 1: Metadata-only tagging (fast, no network)

- Read `starred_repos.json`
- Match tags from taxonomy using keyword/topic/language matching
- Generate all Obsidian tag notes
- Track repos with few/no tags for Phase 2

### Phase 2: README fetch + enrichment

- Fetch README from raw.githubusercontent.com for all repos
- Save README to `stars/readme/owner_repo.md`
- Extract additional tags from README content
- Update tag notes with enriched tags
- Repos with no README: save empty placeholder, record in `untagged.json`

### Phase 3: Review

- Output `untagged.json` — repos that couldn't be tagged
- Output `misc_tagged.json` — repos tagged with misc
- Output `ambiguous.json` — repos needing manual classification

## Matching Priority

1. GitHub Topics direct match against taxonomy
2. Language metadata match
3. Description keyword match against taxonomy keywords
4. README keyword match (Phase 2)

## Rate Limiting

- Phase 1: no network requests, instant
- Phase 2: 0.5s delay between README fetches
- Raw GitHub content (raw.githubusercontent.com) has no auth requirement and higher rate limits
- On 403 rate limit: wait 60s and retry

## Repo Count

Dynamic — based on actual fetched count from GitHub API, not hardcoded.
