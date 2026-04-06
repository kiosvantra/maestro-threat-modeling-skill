---
name: threat-modeling
description: >
  Domain-neutral threat modeling and risk assessment workflow for environments,
  repositories, or GitHub targets. Trigger: when asked to evaluate risk,
  review trust boundaries, assess threats, or analyze an environment/repo with
  a structured methodology.
license: Apache-2.0
metadata:
  author: gentleman-programming
  version: "1.0"
---

## When to Use

- Evaluating a local environment, repository, or GitHub project
- Assessing security, abuse, or operational risk before changes
- Reviewing trust boundaries, data flows, and external dependencies
- Producing a structured risk report for technical or research domains

## Critical Patterns

Anchor the analysis in a MAESTRO-style decomposition, but keep it adaptive:
- use a boundary-first analysis as the default mode
- model the system as roles, trust boundaries, flows, and attack paths
- follow how delegation, memory, and tools move across those boundaries
- treat the result as a risk narrative, not a rigid checklist
- when useful for comparability, add an optional MAESTRO seven-layer overlay without replacing the boundary-first view

Use this shape when analyzing:
1. Scope and intent
   - what is being assessed
   - what success looks like
   - what is explicitly out of scope

2. System map
   - actors / agents / operators
   - storage and memory
   - tools / APIs / automation
   - external dependencies
   - outputs and side effects

3. Trust boundaries
   - where trust changes
   - where untrusted input becomes privileged action
   - where state persists across tasks or sessions

4. Optional MAESTRO layer mapping
   - map the target to the seven MAESTRO layers when this improves clarity or comparability
   - Foundation Models
   - Data Operations
   - Agent Frameworks
   - Deployment & Infrastructure
   - Evaluation & Observability
   - Security & Compliance
   - Agent Ecosystem
   - mark layers as not applicable when forcing the mapping would reduce accuracy

5. Threats by boundary
   - spoofing, tampering, disclosure, repudiation, DoS, privilege escalation
   - prompt injection, tool abuse, unsafe automation
   - supply-chain risk, misconfiguration, and drift
   - when useful, distinguish traditional threats from agentic threats

6. Impact and likelihood
   - impact
   - likelihood
   - exposure
   - blast radius
   - detection gaps

7. Mitigations
   - least privilege
   - validation / normalization
   - scope isolation
   - auditability
   - safe defaults / fail-closed behavior
   - rollback / recovery

8. Deliverables
   - concise executive summary
   - technical report
   - optional MAESTRO layer summary or layer-by-layer table
   - optional boundary-to-layer crosswalk when both views are used
   - optional issue candidates when action is clear

9. Reporting rules
   - distinguish facts from assumptions
   - preserve source labels
   - call out open questions
   - separate systemic risk from local risk
   - if using MAESTRO layers, do not let the layer view override clearer boundary evidence

## Workflow

- Start with the target type (repo, environment, research corpus, or GitHub target).
- Default to a boundary-first analysis; use the MAESTRO layer overlay only when it adds comparability, coverage, or stakeholder clarity.
- Use retrieval and memory if available, but never confuse them with evidence.
- Focus on what can fail, be abused, or leak across boundaries.
- If the seven-layer MAESTRO view is used, keep it as a second lens rather than the primary source of truth.
- When appropriate, label findings as traditional or agentic to match MAESTRO-style reporting.
- Keep the language domain-neutral and the output reusable.
- If the boundary is unclear, ask for it before making conclusions.
- Prefer the shortest report that still explains the real risk.

## Output Naming Convention

Use a stable, domain-neutral file name format:

`YYYY-MM-DD_<scope>_<target>_<artifact>.md`

Where:
- `scope` is one of `global`, `project`, `environment`, or `repo`
- `target` is a short stable name for the thing being analyzed
- `artifact` is one of `summary`, `full-report`, or `obsidian-note`

Examples:
- `2026-04-05_global_cybersecurity_summary.md`
- `2026-04-05_project_metronous_full-report.md`
- `2026-04-05_environment_opencode_obsidian-note.md`
- `2026-04-05_repo_github-foo_full-report.md`

## Commands

```bash
# Inspect a local repository
git status --short
git log --oneline -n 5

# Inspect a GitHub target
gh repo view OWNER/REPO
gh issue list --repo OWNER/REPO

# Optional: gather extra context from your own retrieval system
# <your-retrieval-command> "<topic>"
```

## Resources

- **Methodology notes**: apply the OWASP agentic AI threat taxonomy to multi-agent systems, with MAESTRO-style decomposition of the system into roles, flows, trust boundaries, and attack paths
- **Templates**: see `assets/obsidian-note-template.md` and `assets/technical-report-template.md`
- **Retrieval**: optional, bring your own retrieval layer if applicable
- **Memory**: optional, use your preferred memory or notes system when prior decisions matter

## Closing Behavior

After finishing the report, if any finding is actionable, ask:

> Do you want me to open detailed issues for this repo?

If the answer is yes, convert the findings into concrete GitHub issues with:
- a short title
- clear impact
- evidence or reproduction notes
- suggested mitigation
- priority/severity
- related files or components when known
