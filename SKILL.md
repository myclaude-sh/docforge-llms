---
name: docforge-llms
display_name: Docforge Llms
description: "Project canonical Markdown docs into AI-native projections — llms.txt (Howard 2024 spec), llms-full.txt (segmented), AGENTS.md (AAIF/Linux Foundation Dec 2025), CLAUDE.md (Anthropic verbatim, ≤200 lin"
version: 0.1.0
author: l0z4n0
license: Proprietary
tags:
  - "llms.txt"
  - "AGENTS.md"
  - "CLAUDE.md"
  - "MCP"
  - "RAG"
  - "prompt-cache"
  - "documentation"
  - "dual-output"
marketplace_url: "https://myclaude.sh/p/docforge-llms"
user-invocable: true
---

# `docforge-llms` — sub-skill of `docforge`

Canonical Markdown → AI-native projections (llms.txt, AGENTS.md, CLAUDE.md, MCP, .cursor/rules, .github/copilot-instructions, per-page .md).

**One canonical. Many projections. Audience declared, or refused.**

## Layout

```
docforge-llms/
├── SKILL.md                  # Body. ≤500 lines. Lazy-loads references.
├── README.md                 # This file.
├── references/               # Progressive-disclosure deepdives (load on demand).
│   ├── llms-txt-spec.md
│   ├── claude-md-anthropic.md
│   ├── agents-md-spec.md
│   ├── mcp-spec-essentials.md
│   ├── cache-economics.md
│   ├── chunkability-rules.md
│   └── dual-output-pattern.md
├── templates/                # Output templates with deterministic placeholders.
│   ├── llms-txt.template
│   ├── llms-full-segmented.template
│   ├── claude-md.template
│   ├── agents-md.template
│   ├── cursor-rules.template.mdc
│   ├── copilot-instructions.template.md
│   └── mcp-server.template.py
├── scripts/                  # Capability implementations.
│   ├── project.py            # canonical → per-page .md + llms.txt
│   ├── forge_agents_md.py
│   ├── forge_claude_md.py
│   ├── mcp_scaffold.py
│   ├── chunkability_lint.py
│   ├── cache_optimize.py
│   ├── diagram_alt_referencer.py
│   └── lib/
│       ├── frontmatter.py
│       ├── tone_transformer.py
│       └── token_counter.py
├── audiences/                # Per-audience profiles (knobs for tone transformer).
│   ├── llm-runtime.profile.yaml
│   ├── llm-rag.profile.yaml
│   ├── human-novice.profile.yaml
│   ├── human-expert.profile.yaml
│   └── ci.profile.yaml
└── tests/                    # Smoke tests.
```

## Capabilities (v0.1)

| Capability | Priority | One-liner |
|------------|----------|-----------|
| `project` | P0 | Emit per-page `.md` + `llms.txt` + opt. `llms-full.txt` |
| `forge-agents-md` | P0 | AAIF-spec `AGENTS.md` |
| `forge-claude-md` | P0 | `CLAUDE.md` ≤200 lines, imports `@AGENTS.md` |
| `mcp-scaffold` | P1 | Python MCP server, docs as `resources` |
| `chunkability-lint` | P0 | 10-rule lint for RAG-friendly writing |
| `cache-optimize` | P1 | Payload ordering for prompt-cache hits (90% savings) |

## Invariants

I1 audience-declared · I2 canonical=MD-in-git · I3 CLAUDE.md ≤200 lines · I4 AGENTS.md is canonical · I5 llms.txt = Howard spec · I6 MCP typed · I7 cache-aware order · I8 provenance tag · I9 no human edits a projection.

See `SKILL.md §1` for the full table.

## Sources (verbatim references)

- llms.txt spec — Howard / Answer.AI 2024 → `references/llms-txt-spec.md`
- CLAUDE.md — Anthropic verbatim → `references/claude-md-anthropic.md`
- AGENTS.md — AAIF / Linux Foundation Dec 2025 → `references/agents-md-spec.md`
- MCP — modelcontextprotocol.io 2025-11-25 → `references/mcp-spec-essentials.md`
- Cache economics — Anthropic prompt-caching docs → `references/cache-economics.md`

## Refuses

- No `audience` declared → refuse.
- CLAUDE.md target >200 lines → refuse.
- `forge-claude-md` without AGENTS.md → refuse.
- Edit a projection by hand → refuse. Edit canonical, regenerate.

<!-- generated:llm reviewed:human@HEAD -->

---

[![MCS-2](https://myclaude.sh/badge/mcs/2.svg)](https://myclaude.sh/quality)
[![Available on MyClaude](https://myclaude.sh/badge/available.svg)](https://myclaude.sh/p/docforge-llms)

<sub>Built with MyClaude Studio Engine</sub>

