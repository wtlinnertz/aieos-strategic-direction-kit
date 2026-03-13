# Strategic Direction Kit

An [AIEOS](https://github.com/wtlinnertz/aieos-governance-foundation) kit for governing strategic investment decisions. Layer 1 of the AIEOS system.

## What It Does

Transforms informal strategic intent into falsifiable, measurable bets with explicit prioritization and capacity constraints. Feeds the Product Intelligence Kit (Layer 2) with funded strategic direction.

## Artifacts

| Artifact | Purpose | Hard Gates |
|----------|---------|-----------|
| **Strategic Bet Record (SBR)** | Captures a single falsifiable bet | 6 (thesis falsifiable, success signal measurable, failure signal defined, time horizon bounded, investment envelope stated, single accountable owner) |
| **Portfolio Prioritization Record (PPR)** | Ranks all active bets | 5 (strict rank order, trade-off rationale, cut line explicit, capacity not exceeded, review trigger defined) |

## Anti-Bureaucracy Design

- **Two artifacts, not five.** SBR + PPR. That's it.
- **Failure signals are mandatory.** If you can't say what would make you stop, the bet isn't ready.
- **No ties in prioritization.** Tiers are politics. The PPR forces a strict rank order.
- **Signal-driven review.** Re-prioritize when signals warrant it, not when the calendar says so.
- **180-day expiration.** Unreferenced SBRs expire. No zombie bets.

## Getting Started

See [`docs/playbook.md`](docs/playbook.md) for the complete process.

## Part of AIEOS

This kit follows the [AIEOS Governance Model](https://github.com/wtlinnertz/aieos-governance-foundation). See the governance foundation for structural rules, the four-file system, and inter-kit contracts.
