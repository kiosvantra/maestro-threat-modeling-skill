---
name: maestro-threat-modeling-canonical
description: >
  Canonical threat-modeling workflow combining boundary-first analysis with a
  MAESTRO overlay, optimized for repo-first assessments and reusable across
  repositories, environments, GitHub targets, and CISO workflows.
license: MIT
metadata:
  author: Igris
  version: "2.0.0"
---

# MAESTRO Threat Modeling — Canonical

Use this as the canonical threat-modeling skill when asked to assess security, abuse, or operational risk in a **repository**, **environment**, **GitHub target**, or adjacent technical system.

## Core stance
- Default to a **boundary-first analysis**.
- Use the **MAESTRO layer model as an overlay**, not as theater.
- Treat the output as a **risk narrative grounded in evidence**, not a rigid checklist.
- For repo work, present the result explicitly as **repo-first** unless runtime evidence was also inspected.

## Best-fit use cases
- repo threat modeling
- CISO repo reviews
- agentic / multi-agent systems
- RAG pipelines
- MCP / tool-calling systems
- deployment and CI/CD reviews
- GitHub-target risk review

## Required output shape
Always structure the result in this order:
1. **Scope and intent**
2. **System snapshot**
3. **Trust boundaries**
4. **Assumptions and blind spots**
5. **MAESTRO layer findings**
6. **Top threats**
7. **Mitigations**
8. **Execution backlog**

## Evidence rules
- Prefer direct evidence: code, configs, workflows, prompts, manifests, docs, infra files, logs, issue history.
- Distinguish clearly between **facts**, **inferences**, and **assumptions**.
- Never claim a control exists unless the target shows it.
- Retrieval, memory, or prior notes can help orientation, but they are not evidence by themselves.

## Boundary-first method
Model the target as:
- roles / actors / agents / operators
- storage and memory
- tools / APIs / automations
- external dependencies
- outputs and side effects
- trust boundaries
- attack paths across those boundaries

Focus on:
- where untrusted input becomes privileged action
- where state persists across tasks or sessions
- where memory, delegation, or tools cross trust zones
- where blast radius can spread laterally

## MAESTRO overlay
Use MAESTRO only when it improves clarity or comparability.
If a layer does not fit, mark it not applicable.

### 1. Foundation / Models
Look for:
- model/provider definitions
- routing logic
- system prompts / instructions
- safety guardrails
- fallback behavior

Typical risks:
- unsafe prompt composition
- weak trust-tier separation
- missing high-risk guardrails

### 2. Data Operations
Look for:
- RAG pipelines
- vector stores
- memory systems
- ingestion logic
- trust boundaries around documents and context assembly

Typical risks:
- prompt injection
- retrieval poisoning
- memory poisoning
- cross-context leakage

### 3. Agent Frameworks
Look for:
- tool-calling definitions
- delegation loops
- autonomy boundaries
- role separation
- orchestration logic

Typical risks:
- tool misuse
- privilege confusion
- unsafe delegation
- weak approval boundaries

### 4. Deployment & Infrastructure
Look for:
- Dockerfiles
- compose/k8s manifests
- service units
- reverse proxy config
- network exposure
- secret paths
- CI/CD defaults

Typical risks:
- exposed ports
- permissive file modes
- weak isolation
- unsafe defaults
- brittle secret handling

### 5. Evaluation & Observability
Look for:
- logs
- traces
- audit trails
- issue comments
- run artifacts
- security review outputs

Typical risks:
- poor traceability
- repudiation / untraceability
- inability to reconstruct incidents
- missing review evidence

### 6. Security & Compliance
Look for:
- auth patterns
- authorization boundaries
- secret management
- policy checks
- dependency and supply-chain controls

Typical risks:
- auth bypass
- overprivileged services
- uncontrolled secret sprawl
- silent policy drift

### 7. Agent Ecosystem
Look for:
- multi-agent interactions
- external agents or bots
- cross-repo integrations
- MCP/server trust assumptions

Typical risks:
- ecosystem trust collapse
- spoofed agent identity
- toxic tool or agent chaining
- lateral compromise across agents

## Threat classes to check
Include traditional and agentic threats when relevant:
- spoofing
- tampering
- disclosure
- repudiation
- denial of service
- privilege escalation
- prompt injection
- tool abuse
- unsafe automation
- supply-chain risk
- misconfiguration
- drift

## Severity model
Use:
- `critical`
- `high`
- `medium`
- `low`
- `accepted-risk`

Evaluate severity from:
- exploitability
- blast radius
- privilege level
- detectability gap
- operational impact

## Output template

```markdown
# Threat Model — <target>

## Scope and intent
- Target:
- Assessment mode: repo-first | runtime-assisted | environment | GitHub target
- Goal:
- Out of scope:

## System snapshot
- Purpose:
- Security-relevant components:
- Key integrations:

## Trust boundaries
- Boundary 1:
- Boundary 2:
- Boundary 3:

## Assumptions and blind spots
- Runtime not inspected:
- Live secrets not validated:
- Network exposure inferred from config only:

## MAESTRO layer findings
### Foundation / Models
- Evidence:
- Risks:

### Data Operations
- Evidence:
- Risks:

### Agent Frameworks
- Evidence:
- Risks:

### Deployment & Infrastructure
- Evidence:
- Risks:

### Evaluation & Observability
- Evidence:
- Risks:

### Security & Compliance
- Evidence:
- Risks:

### Agent Ecosystem
- Evidence:
- Risks:

## Top threats
1. `<severity>` — threat title
   - Evidence:
   - Why it matters:
   - Boundary:
   - MAESTRO layer:

## Mitigations
- Immediate:
- Near-term:
- Structural:

## Execution backlog
- [ ] critical:
- [ ] high:
- [ ] medium:
```

## Repo-first note
If the target is a repo, explicitly state:
- this is a **repo-first threat model**
- runtime conclusions are limited to visible evidence
- missing runtime validation remains a blind spot

## GitHub / issue conversion
If the findings are clearly actionable, offer to convert them into issues with:
- concise title
- impact
- evidence
- mitigation
- severity
- affected files/components

## Success criterion
A good result is:
- evidence-based
- boundary-first
- MAESTRO-aligned without becoming rigid
- explicit about blind spots
- short enough to act on
- reusable by the CISO or outside the CISO role
