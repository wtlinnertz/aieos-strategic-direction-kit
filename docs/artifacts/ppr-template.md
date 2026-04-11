# Portfolio Prioritization Record

## §1 Document Control

| Field | Value |
|-------|-------|
| Artifact ID | PPR-{NNN} |
| Status | Draft / Validated / Freeze Pending / Frozen |
| Author | {name} |
| Portfolio Owner | {single named individual} |
| Date | {YYYY-MM-DD} |
| Governance Model Version | {from governance-model.md §15} |
| Spec Version | {from ppr-spec.md} |
| Principles Version | {from strategic-direction-principles.md} |

## §2 Active Bet Inventory

| SBR ID | Thesis Summary | Time Horizon | Investment Envelope | Status |
|--------|---------------|-------------|--------------------| -------|
| {SBR ID} | {one-sentence thesis} | {duration} | {resource scope} | Frozen |

## §3 Ranked Bet List

| Rank | SBR ID | Thesis Summary |
|------|--------|---------------|
| 1 | {SBR ID} | {one-sentence thesis} |
| 2 | {SBR ID} | {one-sentence thesis} |
| ... | ... | ... |

## §4 Trade-Off Rationale

| Pair | Rationale |
|------|-----------|
| Rank 1 vs Rank 2 | {1-3 sentences: why rank 1 is above rank 2} |
| Rank 2 vs Rank 3 | {1-3 sentences: why rank 2 is above rank 3} |
| ... | ... |

## §5 Capacity Allocation

| Field | Value |
|-------|-------|
| Total Available Capacity | {teams, budget, time} |

| Rank | SBR ID | Capacity Assignment |
|------|--------|-------------------|
| 1 | {SBR ID} | {resource allocation} |
| 2 | {SBR ID} | {resource allocation} |
| ... | ... | ... |

| Field | Value |
|-------|-------|
| Total Allocated | {sum of assignments} |
| Remaining | {total - allocated} |

## §6 Cut Line

| Field | Value |
|-------|-------|
| Cut Line Position | After Rank {N} |
| Funded Bets | {count} |
| Deferred Bets | {count} |

**Above the line (funded):** {list of SBR IDs}

**Below the line (deferred):** {list of SBR IDs}

## §7 Review Trigger

| Trigger | Description |
|---------|-------------|
| {trigger type} | {specific condition that causes re-prioritization} |

Next scheduled review: {date or "triggered by above conditions"}
