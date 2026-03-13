# Portfolio Prioritization Record Spec

Version: v1.0

## Purpose

The Portfolio Prioritization Record (PPR) is a ranked list of active Strategic Bet Records with explicit trade-offs and a capacity cut line. One PPR per prioritization cycle. The PPR is the handoff artifact to the Product Intelligence Kit — above-the-line bets are funded and routed to discovery.

## Upstream Dependencies

- At least 2 frozen Strategic Bet Records (SBRs)

## Downstream Dependents

- PIK Discovery Intake — references the PPR line item as strategic context

## Sections

### §1 Document Control

Standard AIEOS Document Control section.

Required fields: Artifact ID, Status, Author, Portfolio Owner, Date, Governance Model Version, Spec Version, Principles Version.

The Portfolio Owner is a single named individual who owns the rank order. This is the person accountable for the prioritization decision.

### §2 Active Bet Inventory

A complete list of all frozen SBRs eligible for prioritization.

Rules:
- Every non-expired, non-abandoned frozen SBR must be listed
- Each entry includes: SBR ID, thesis summary (one sentence), time horizon, investment envelope
- Omitting a valid frozen SBR from the inventory is a hard gate failure

### §3 Ranked Bet List

A strict rank-ordered list of SBRs from highest to lowest priority.

Rules:
- Strict rank order — no ties, no tiers, no "equal priority" groupings
- Every SBR in §2 must appear exactly once in the ranking
- Rank 1 is the highest priority

### §4 Trade-Off Rationale

For each adjacent pair in the ranking (rank 1 vs 2, rank 2 vs 3, etc.), a brief rationale explaining why the higher-ranked bet is above the lower-ranked bet.

Rules:
- Every adjacent pair must have a rationale — no gaps
- Rationale must reference specific factors (evidence, urgency, strategic alignment, risk, capacity fit) — not generic statements like "more important"
- 1-3 sentences per pair

### §5 Capacity Allocation

Maps above-the-line bets to available capacity.

Rules:
- Must state total available capacity (teams, budget, time)
- Each above-the-line bet must have a capacity assignment that fits within the total
- The sum of capacity assignments must not exceed total available capacity

### §6 Cut Line

The explicit boundary between funded and deferred bets.

Rules:
- Must identify the exact position in the ranking where funded bets end and deferred bets begin
- Bets above the line are funded and will be routed to PIK
- Bets below the line are deferred — not "stretch goals", not "nice to have"
- If all bets are funded, the cut line is stated as "all bets above the line" with a capacity justification

### §7 Review Trigger

What event or signal causes the next re-prioritization.

Rules:
- Must define at least one trigger (not just "next quarter")
- Valid triggers: IEK re-discover signal, SBR time horizon expiry, significant market event, capacity change, new SBR creation
- Calendar-based triggers are permitted as a backstop but must not be the sole trigger

## Artifact ID Format

`PPR-{NNN}`

Examples: `PPR-001`, `PPR-002`

## Hard Gates

| Gate | Rule |
|------|------|
| `strict_rank_order` | §3 is a strict total order — no ties, no tiers; every SBR in §2 appears exactly once |
| `trade_off_rationale_present` | §4 provides a rationale for every adjacent pair in the ranking |
| `cut_line_explicit` | §6 identifies the exact cut line position; below-the-line bets are deferred, not ambiguous |
| `capacity_not_exceeded` | §5 capacity assignments for above-the-line bets do not exceed stated total capacity |
| `review_trigger_defined` | §7 defines at least one non-calendar-only trigger for re-prioritization |
