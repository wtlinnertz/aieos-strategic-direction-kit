# Technology Investment Roadmap — Spec

Version: v1.0

## Purpose

The Technology Investment Roadmap (TIR) defines technology investments that enable product capabilities over a 2-5 year horizon. It classifies every technology area in scope as adopt, hold, or retire — ensuring that technology decisions are driven by traced business needs, not resume-driven engineering.

## Upstream Dependencies

- Frozen Product Capability Roadmap (PCR) — required
- Frozen Capability Landscape Assessment (CLA) — recommended
- PINFK Platform Decision Records (PDRs) — optional (existing technology decisions)

## Downstream Dependents

- PINFK PDR creation — new technology decisions resulting from adopt/retire classifications
- EEK Architecture Constraint Framework (ACF) — technology constraints from TIR classifications

## Sections

### §1 Document Control

Standard AIEOS Document Control section.

Required fields: Artifact ID, Status, Author, Technology Owner, Date, Horizon, Governance Model Version, Spec Version, Principles Version.

The Technology Owner is a single named individual accountable for the technology investment roadmap — not a committee, not a team name, not a role title without a person attached.

The Horizon field states the planning window: 2-5yr. This sets the outer boundary for investment timeframes in §2.

### §2 Technology Landscape

A table of all technology areas in scope with their current state, target state, and investment classification.

Required columns: Area, Current State, Target State, Classification, Driver, Investment Level, Timeframe.

Rules:
- **Area**: A named technology area — concise, noun-phrase form (e.g., "Message Queue Infrastructure", "Frontend Framework", "Observability Stack")
- **Current State**: A brief description of what is in place today
- **Target State**: A brief description of the desired future state within the horizon
- **Classification**: Exactly one of: `adopt` (new technology to introduce), `hold` (continue current investment, no change), `retire` (phase out and replace)
- **Driver**: The business or capability need this investment serves. Must trace to a PCR capability or an operational need — not a technology preference.
- **Investment Level**: One of: `major` (significant effort and budget), `moderate` (meaningful but bounded), `minor` (low effort, incremental)
- **Timeframe**: A target window for the investment — quarter, half, or year

### §3 Adoption Plans

One entry per technology classified as "adopt" in §2.

Rules:
- Each adoption plan must include: evaluation criteria (what must be true for the technology to be selected), POC plan (scope, timeline, success criteria), rollout timeline (phases, milestones)
- Evaluation criteria must be measurable — not "best in class" or "modern"
- POC plan must be bounded — not open-ended exploration
- If no technologies are classified as "adopt", state "No adoption plans — all technologies are hold or retire"

### §4 Retirement Plans

One entry per technology classified as "retire" in §2.

Rules:
- Each retirement plan must include: migration path (what replaces it and how), timeline (phases with dates), affected systems (what depends on the retiring technology), risk assessment (what could go wrong during migration)
- Migration path must identify the replacement — "TBD" is not accepted for the replacement identity, though detailed implementation may be deferred
- If no technologies are classified as "retire", state "No retirement plans — all technologies are hold or adopt"

### §5 PCR Alignment

A mapping between TIR technology investments and PCR product capabilities.

Rules:
- Every "adopt" technology must map to at least one PCR capability it enables
- Every PCR capability with a technology dependency must have a corresponding TIR entry
- Gaps in either direction must be explicitly identified and justified
- The mapping must be bidirectional — from TIR to PCR and from PCR to TIR

## Artifact ID Format

`TIR-{SCOPE}-{NNN}`

Examples: `TIR-PLATFORM-001`, `TIR-FRONTEND-001`, `TIR-INFRASTRUCTURE-001`

## Hard Gates

| Gate | Rule |
|------|------|
| `investment_inventory` | Every technology area in scope is listed in §2; no known technologies silently omitted |
| `driver_traced` | Every investment in §2 traces to a PCR capability or operational need; no investment without a business driver |
| `classification_present` | Every technology in §2 has exactly one classification: adopt / hold / retire |
| `migration_paths` | Every "retire" technology in §2 has a retirement plan in §4 with: migration path, timeline, affected systems, risk assessment |
| `pcr_alignment` | Every "adopt" technology maps to at least one PCR capability in §5; every PCR capability with a technology dependency has a corresponding TIR entry |

## Lifecycle

The TIR is re-frozen annually or when the PCR undergoes material changes that affect technology requirements.
