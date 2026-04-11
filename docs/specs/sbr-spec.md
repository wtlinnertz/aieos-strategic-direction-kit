# Strategic Bet Record Spec

Version: v1.0

## Purpose

The Strategic Bet Record (SBR) captures a single strategic bet — a falsifiable thesis about what the organization should invest in and why. One SBR per strategic theme. The SBR is the smallest unit of strategic direction that AIEOS governs.

## Upstream Dependencies

None. The SBR is the entry point for the AIEOS pipeline. External inputs (board direction, market data, IEK feedback, customer signals) inform the SBR but are not governed artifacts.

## Downstream Dependents

- Portfolio Prioritization Record (PPR) — ranks frozen SBRs

## Sections

### §1 Document Control

Standard AIEOS Document Control section.

Required fields: Artifact ID, Status, Author, Executive Sponsor, Date, Governance Model Version, Spec Version, Principles Version.

The Executive Sponsor field replaces the standard Owner field. The sponsor is a single named individual accountable for the bet — not a committee, not a team name, not a role title without a person attached.

### §2 Thesis

A single falsifiable statement in the form: "We believe [action] will produce [outcome] because [evidence]."

Rules:
- Must be one statement, not a list of aspirations
- Must be falsifiable — if it cannot be proven wrong, it is not a thesis
- The [evidence] component must reference observable data, not assumptions or beliefs
- Must not reference specific solutions or implementations (those are downstream concerns)

### §3 Success Signal

A measurable indicator that the bet is working.

Rules:
- Must reference a specific, observable metric (not "increase engagement" or "improve satisfaction")
- Must include a target threshold or direction (e.g., "reduction in support tickets from >50/week to <20/week")
- Must be measurable within the stated time horizon (§5)
- One primary signal. Secondary signals are permitted but must be clearly labeled

### §4 Failure Signal

A measurable indicator that the bet should be abandoned or pivoted.

Rules:
- Must be defined — blank or "N/A" is not accepted
- Must be falsifiable and measurable (same standard as success signal)
- Must describe what would cause the organization to stop investing, not merely slow down
- Must be distinguishable from the success signal (not simply its inverse)

### §5 Time Horizon

When the organization expects to see the success or failure signal.

Rules:
- Must be a bounded duration (e.g., "6 months", "Q3 2026") — open-ended is not accepted
- Must be realistic relative to the investment envelope (§6)
- Triggers mandatory review: when the time horizon expires, the SBR must be re-evaluated (renew, pivot, or abandon)

### §6 Investment Envelope

Rough resource scope for the bet — not a detailed budget.

Rules:
- Must state the approximate team allocation (e.g., "1 team for 1 quarter", "2 engineers for 6 months")
- Must not be unbounded ("as needed" is not accepted)
- Precision is intentionally low — this is a strategic input, not a project plan
- May include capital/expense category if relevant to the organization

### §7 Strategic Context

What organizational goal, constraint, or external signal this bet serves.

Rules:
- Must reference a specific organizational goal, board directive, market signal, or IEK feedback (not generic statements like "align with company strategy")
- If triggered by an IEK re-discover signal, must cite the ES artifact ID
- Brief — 2-4 sentences maximum. The context is a pointer, not a restatement of organizational strategy

### §8 Expiration

Rules:
- Unreferenced SBRs (not included in any frozen PPR) expire after 180 days from freeze date
- Active SBRs (referenced in a frozen PPR) are governed by their time horizon (§5)
- Expired SBRs transition to Abandoned status. They may be re-created as new SBRs with new IDs if the bet is still relevant.

## Artifact ID Format

`SBR-{THEME}-{NNN}`

Examples: `SBR-MOBILE-EXPANSION-001`, `SBR-API-PLATFORM-001`, `SBR-COST-REDUCTION-001`

## Hard Gates

| Gate | Rule |
|------|------|
| `thesis_falsifiable` | §2 contains a single falsifiable thesis in the required form; it can be proven wrong by observable evidence |
| `success_signal_measurable` | §3 references a specific, observable metric with a target threshold or direction |
| `failure_signal_defined` | §4 defines a measurable condition that would cause the bet to be abandoned — not blank, not "N/A", not the inverse of the success signal |
| `time_horizon_bounded` | §5 states a specific bounded duration — not open-ended |
| `investment_envelope_stated` | §6 states approximate resource scope — not "as needed" or unbounded |
| `single_accountable_owner` | §1 Executive Sponsor names one individual — not a committee, not a team, not a vacant role |
