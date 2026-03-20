# Capability Lifecycle Assessment — Spec

Version: v1.0

## Purpose

The Capability Lifecycle Assessment (CLA) catalogs all existing capabilities for a product or service, assigns a lifecycle decision to each (invest, maintain, sunset, or retire), and identifies roadmap inputs. The CLA is the retroactive onboarding artifact — existing products enter AIEOS through the CLA. One CLA per product or service boundary.

## Upstream Dependencies

None required. The CLA is the entry point for retroactive onboarding of existing products into the AIEOS pipeline. Optional inputs that strengthen lifecycle decisions: IEK Evolution Signal (ES) files, RRK Reliability Health Review (RHR) files, existing product documentation.

## Downstream Dependents

- Portfolio Prioritization Record (PPR) — §5 invest decisions feed PCR capability entries
- Technology Investment Record (TIR) — sunset/retire decisions may trigger technology retirement planning

## Sections

### §1 Document Control

Standard AIEOS Document Control section.

Required fields: Artifact ID, Status, Author, Assessment Owner, Date, Governance Model Version, Spec Version, Principles Version.

The Assessment Owner is a single named individual accountable for the lifecycle decisions in this CLA — not a committee, not a team name, not a role title without a person attached.

### §2 Capability Inventory

A complete catalog of all known capabilities for the product or service.

Rules:
- Every known capability must be listed — no silent omissions
- If a gap is acknowledged (a capability is suspected to exist but details are unknown), it must be listed with a "Gap — {reason}" note in the Description field
- The inventory must originate from user/operator input, not AI inference. AI may structure, categorize, and assess, but the raw capability list must trace to human knowledge
- Each entry includes: Name, Description, Owner (person or team), Users (who uses this capability), IEK Signal (ES artifact ID or "None"), RRK Signal (RHR artifact ID or "None"), Lifecycle Decision, Rationale

### §3 Sunset Plans

For every capability marked "sunset" or "retire" in §2, a plan for removal.

Rules:
- One subsection per sunset/retire capability
- Each plan must include: timeline (bounded — not "when convenient"), migration path (what users should do instead), affected users (specific list from §2 Users column), communication plan reference (how affected users will be notified)
- If there is no migration path (the capability is being retired without replacement), this must be stated explicitly as "No replacement — {justification}"
- Timeline must be bounded — "eventually" or "TBD" is not accepted

### §4 Capacity Implications

What capacity does each lifecycle decision imply?

Rules:
- Must address both sides: what capacity do sunset/retire decisions free up, and what capacity do invest decisions require
- Capacity is stated at strategic precision (team-months, headcount bands, cost ranges) — not project-level detail
- If sunset/retire frees zero capacity (e.g., the capability runs unattended), this must be stated explicitly
- Must not double-count: capacity freed by sunset cannot be simultaneously allocated to two invest decisions

### §5 Roadmap Inputs

Which lifecycle decisions should produce downstream artifacts?

Rules:
- Every "invest" decision must state whether it should become a PCR entry (new bet or enhancement to an existing bet), and if not, why not
- Every "sunset" or "retire" decision must state whether it affects any existing PCR entries or active SBRs
- "Maintain" decisions do not require roadmap entries but may note if the maintenance burden is trending toward an invest or sunset decision
- This section produces the handoff material for PPR integration

## Lifecycle

The CLA is a living document. It is frozen upon initial completion, then re-frozen:
- Semi-annually (minimum cadence)
- When IEK produces new Evolution Signal (ES) artifacts relevant to inventoried capabilities
- When material changes occur (capability added, removed, or lifecycle decision changed)

Version increments on each re-freeze: v1, v2, v3, etc.

## Artifact ID Format

`CLA-{PRODUCT}-{NNN}`

Examples: `CLA-TASKFLOW-001`, `CLA-BILLING-PLATFORM-001`, `CLA-MOBILE-APP-001`

## Hard Gates

| Gate | Rule |
|------|------|
| `capability_inventory` | §2 lists every known capability with owner and description; gaps are acknowledged with justification, not silently omitted |
| `user_provided_inventory` | §2 capability inventory originates from user/operator input, not AI inference. The raw capability list traces to human knowledge. AI may structure and categorize but must not invent the inventory. |
| `lifecycle_decision` | Every capability in §2 has exactly one lifecycle decision: invest, maintain, sunset, or retire — no blanks, no "TBD", no multiple decisions |
| `signal_basis` | Every lifecycle decision cites specific evidence. Acceptable sources: IEK ES signal (with artifact ID), RRK RHR pattern (with artifact ID), usage data (with metric), market signal (with source), team/stakeholder input (with attribution). For initial assessments without AIEOS history: "Initial assessment — {specific evidence}" where specific evidence is concrete (user count, support ticket volume, revenue contribution, team feedback with attribution). Vague "initial assessment" without specifics FAILS. |
| `sunset_plans` | Every capability marked "sunset" or "retire" in §2 has a corresponding plan in §3 with: timeline (bounded), migration path (or explicit "no replacement" with justification), affected users listed, communication plan reference |
| `no_orphans` | No capability in §2 without an identified owner — person or team name, not "TBD", not "Unknown", not blank |
