# MAESTRO Threat Modeling Skill

<p align="center">
  <img src="assets/maestro-threat-modeling-skill.svg" alt="MAESTRO Threat Modeling Skill banner" width="100%" />
</p>

A portable, public threat-modeling skill for agent workflows.

It is inspired by the Cloud Security Alliance MAESTRO framework, but optimized for practical agent operations: trust boundaries, attack paths, evidence-aware reporting, and optional issue generation.

## What this is

- A single reusable `SKILL.md` for agent frameworks that support skill-style prompts
- A boundary-first threat-modeling workflow with an optional MAESTRO seven-layer overlay
- A portable package with no hard dependency on private memory, retrieval, or local scripts

## What this is not

- Not an official CSA MAESTRO repository
- Not a web app or scanner
- Not a complete security audit by itself

## Core design

This skill keeps the primary analysis centered on:

- roles
- trust boundaries
- data and control flows
- attack paths
- evidence vs assumptions
- mitigations and follow-up issues

When useful, it adds a second lens based on the seven MAESTRO layers:

1. Foundation Models
2. Data Operations
3. Agent Frameworks
4. Deployment & Infrastructure
5. Evaluation & Observability
6. Security & Compliance
7. Agent Ecosystem

## Why this approach

Pure layer-only analysis is useful for consistency, but real-world agent systems often fail at boundaries: where tools become privileged, where memory persists, where delegated actions cross trust zones, and where ambiguous input becomes automation.

This skill treats MAESTRO as a strong comparative lens while preserving boundary-first reasoning as the default mode.

## Repository layout

```text
.
├── SKILL.md
├── README.md
├── LICENSE
└── assets/
    ├── maestro-threat-modeling-skill.svg
    ├── obsidian-note-template.md
    └── technical-report-template.md
```

## Included artifacts

- `SKILL.md` — the portable threat-modeling skill
- `assets/obsidian-note-template.md` — short note template for knowledge bases
- `assets/technical-report-template.md` — fuller report template for technical reviews

## Usage

Copy `SKILL.md` into your agent skill directory, or adapt it into your prompt system.

Typical use cases:

- analyze a repository before shipping a multi-agent feature
- review an agent environment with tools, memory, and external APIs
- assess a GitHub target with trust-boundary reasoning
- produce actionable findings and convert them into issues

## Output style

Expected outputs include:

- executive summary
- technical report
- optional MAESTRO layer table
- optional boundary-to-layer crosswalk
- optional issue candidates

## Portability notes

This public version intentionally avoids mandatory references to:

- private file paths
- proprietary retrieval systems
- local-only helper scripts
- a specific memory backend

If you have retrieval or memory infrastructure, plug it in as an optional enhancement.

## Recommended workflow

1. Define scope and success criteria
2. Map actors, flows, storage, and side effects
3. Identify trust boundaries
4. Analyze threats by boundary
5. Add MAESTRO layer mapping only if it improves clarity or comparability
6. Score impact, likelihood, exposure, and blast radius
7. Propose mitigations and residual risk
8. Turn clear findings into issues

## Related methodology

- Cloud Security Alliance MAESTRO framework
- OWASP-inspired threat categories for agentic systems
- Boundary-centric threat analysis for tool-using agents

## License

Apache-2.0

## Disclaimer

This repository provides a reusable analysis skill, not a guarantee of security. Human review is still required.
