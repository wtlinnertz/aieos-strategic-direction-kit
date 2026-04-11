# Product Capability Roadmap — Spec

Version: v1.0

## Purpose

The Product Capability Roadmap (PCR) defines what capabilities the product will offer over a 1-3 year horizon, sequenced by timeframe with dependencies. One PCR per product or product area. The PCR translates strategic bets into a structured capability plan that informs downstream prioritization and technology investment decisions.

## Upstream Dependencies

- Frozen Capability Landscape Assessment (CLA) — required
- Roadmap Ideation Record — optional (new opportunity inputs)

## Downstream Dependents

- Strategic Bet Record (SBR) — extraction of individual bets from roadmap themes
- Technology Investment Roadmap (TIR) — alignment of technology investments to planned capabilities

## Sections

### §1 Document Control

Standard AIEOS Document Control section.

Required fields: Artifact ID, Status, Author, Roadmap Owner, Date, Horizon, Governance Model Version, Spec Version, Principles Version.

The Roadmap Owner is a single named individual accountable for the capability roadmap — not a committee, not a team name, not a role title without a person attached.

The Horizon field states the planning window: 1yr, 3yr, or 5yr. This sets the outer boundary for capability timeframes in §3.

### §2 Strategic Themes

A set of organizing themes that group related capabilities.

Rules:
- Each theme must have a name and a brief description (1-2 sentences)
- Themes must trace to organizational strategy, market signals, or CLA findings — not arbitrary groupings
- Themes must be mutually exclusive at the capability level — a capability belongs to exactly one theme
- Minimum 2 themes, maximum 10

### §3 Capability Roadmap

A table of planned capabilities across the planning horizon.

Required columns: Theme, Capability, Description, Target Users, Timeframe, Confidence, Dependencies, Lifecycle Source, Size Estimate.

Rules:
- **Theme**: Must reference a theme defined in §2. No orphan capabilities.
- **Capability**: A named capability — concise, noun-phrase form (e.g., "Bulk Import API", "Self-Service Dashboard")
- **Description**: One sentence describing what the capability delivers to users
- **Target Users**: Who benefits — a named user segment or persona, not "everyone"
- **Timeframe**: A target delivery window — quarter (e.g., "Q2 2026"), half (e.g., "H1 2026"), or year (e.g., "2027"). Entries marked "backlog" must include a justification for why timeframe is not yet assigned.
- **Confidence**: One of: `committed` (funded, planned, in progress or scheduled), `planned` (intended but not yet funded or staffed), `exploratory` (under investigation, no commitment). Each classification must include a brief rationale.
- **Dependencies**: Other capabilities or external dependencies this capability requires. If none, state "None".
- **Lifecycle Source**: For "enhance" or "maintain" capabilities, a CLA entry reference. For "new" capabilities, an ideation output reference, market signal, or strategic directive. Must not be blank.
- **Size Estimate**: T-shirt size (S/M/L/XL) with a brief calibration note (e.g., "L — estimated 2 teams, 1 quarter")

### §4 Dependency Map

A structured view of capability-to-capability and capability-to-external dependencies.

Rules:
- Dependencies must be bidirectional — if capability A depends on capability B, capability B must list A as a dependent
- External dependencies (platform, vendor, regulatory) must be explicitly listed with owner and expected resolution date
- Circular dependencies must be identified and resolved or explicitly flagged with a mitigation plan

### §5 Capacity Assumptions

The resource envelope that constrains what can be delivered within the horizon.

Rules:
- Must state available capacity by timeframe (e.g., teams per quarter, total engineering headcount)
- Must state key constraints (hiring plans, shared resources, seasonal availability)
- Must be explicit — "TBD" or "as available" is not accepted

### §6 Risks and Unknowns

Risks to the roadmap and open questions that could change the plan.

Rules:
- Each risk must have: description, affected capabilities (reference §3 entries), likelihood (high/medium/low), impact (high/medium/low), mitigation approach
- Open unknowns must have: description, what decision or information would resolve them, target resolution date
- Must not be empty — every roadmap has risks. A blank §6 is a hard gate failure.

## Artifact ID Format

`PCR-{PRODUCT}-{NNN}`

Examples: `PCR-PLATFORM-001`, `PCR-MOBILE-001`, `PCR-ANALYTICS-001`

## Hard Gates

| Gate | Rule |
|------|------|
| `theme_coverage` | Every capability in §3 belongs to a strategic theme defined in §2; no orphan capabilities exist |
| `timeframe_assigned` | Every capability in §3 has a target timeframe (quarter, half, or year); entries marked "backlog" include a justification for unbounded timeframe |
| `dependency_mapped` | Dependencies in §4 are bidirectional; if A depends on B, B lists A as dependent; no one-directional dependency references |
| `confidence_justified` | Every capability in §3 has a confidence classification (committed/planned/exploratory) with rationale; committed capabilities reference a frozen CLA entry or frozen SBR |
| `lifecycle_linked` | Every "enhance" or "maintain" capability traces to a CLA entry; every "new" capability traces to an ideation output, market signal, or strategic directive |
| `capacity_realistic` | Total effort of committed + planned capabilities in §3 does not exceed stated capacity in §5; overcommitment fails |

## Lifecycle

The PCR is re-frozen quarterly during planning cycles. Material changes between cycles (new strategic directive, capacity shock, market shift) trigger ad-hoc re-evaluation.
