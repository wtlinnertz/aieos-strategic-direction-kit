# Capability Lifecycle Assessment

## §1 Document Control

| Field | Value |
|-------|-------|
| Artifact ID | CLA-{PRODUCT}-{NNN} |
| Status | Draft / Validated / Freeze Pending / Frozen |
| Author | {name} |
| Assessment Owner | {single named individual} |
| Date | {YYYY-MM-DD} |
| Governance Model Version | {from governance-model.md §15} |
| Spec Version | {from cla-spec.md} |
| Principles Version | {from strategic-direction-principles.md} |

## §2 Capability Inventory

| Name | Description | Owner | Users | IEK Signal | RRK Signal | Lifecycle Decision | Rationale |
|------|-------------|-------|-------|------------|------------|-------------------|-----------|
| {capability name} | {what it does} | {person or team} | {who uses this} | {ES artifact ID or "None"} | {RHR artifact ID or "None"} | {invest / maintain / sunset / retire} | {specific evidence — see spec §2 signal_basis gate} |

## §3 Sunset Plans

### {Capability Name} — {sunset or retire}

| Field | Value |
|-------|-------|
| Lifecycle Decision | {sunset / retire} |
| Timeline | {bounded duration, e.g., "Complete by Q4 2026"} |
| Migration Path | {what users should do instead, or "No replacement — {justification}"} |
| Affected Users | {specific list from §2 Users column} |
| Communication Plan | {reference to communication plan or channel} |

{Repeat subsection for each sunset/retire capability}

## §4 Capacity Implications

### Capacity Freed

| Capability | Decision | Capacity Freed | Notes |
|------------|----------|---------------|-------|
| {name} | {sunset / retire} | {team-months, headcount, cost range} | {or "Zero — runs unattended"} |

### Capacity Required

| Capability | Decision | Capacity Required | Notes |
|------------|----------|------------------|-------|
| {name} | invest | {team-months, headcount, cost range} | {context} |

### Net Capacity Summary

| Field | Value |
|-------|-------|
| Total Freed | {sum of capacity freed} |
| Total Required | {sum of capacity required for invest decisions} |
| Net Impact | {freed minus required} |

## §5 Roadmap Inputs

### Invest Decisions

| Capability | PCR Entry? | Rationale |
|------------|-----------|-----------|
| {name} | {Yes — new bet / Yes — enhancement to {SBR ID} / No — {reason}} | {why this should or should not become a PCR entry} |

### Sunset/Retire Impact on Active Portfolio

| Capability | Affects Existing PCR/SBR? | Details |
|------------|--------------------------|---------|
| {name} | {Yes — {artifact ID} / No} | {impact description} |

### Maintain Watch List

| Capability | Trending Toward | Signal |
|------------|----------------|--------|
| {name} | {invest / sunset / stable} | {what would trigger a decision change} |
