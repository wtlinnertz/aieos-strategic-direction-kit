# Strategic Direction Kit — Index

The Strategic Direction Kit (SDK) governs how an organization captures, validates, and prioritizes strategic bets before committing them to the AIEOS delivery pipeline. It is Layer 1 of the AIEOS system.

## Quick Start

1. Read the [playbook](playbook.md) for the end-to-end process
2. Read the [principles](principles/strategic-direction-principles.md) for organizational policy
3. For AI-assisted authoring, see [how-to-use-with-ai.md](how-to-use-with-ai.md)
4. For organizational adoption, see [how-to-adapt.md](how-to-adapt.md)

## Artifact Types

| Type | Purpose | Hard Gates |
|------|---------|-----------|
| Strategic Bet Record (SBR) | Captures a single falsifiable strategic bet | 6 |
| Portfolio Prioritization Record (PPR) | Ranks all active bets with explicit trade-offs | 5 |

## Key Documents

| Document | Purpose |
|----------|---------|
| [playbook.md](playbook.md) | End-to-end process definition |
| [specs/sbr-spec.md](specs/sbr-spec.md) | SBR content rules and hard gates |
| [specs/ppr-spec.md](specs/ppr-spec.md) | PPR content rules and hard gates |
| [principles/strategic-direction-principles.md](principles/strategic-direction-principles.md) | Organizational strategic direction policy |
| [governance-model.md](governance-model.md) | AIEOS structural rules (synchronized copy) |
| [entry-from-iek.md](entry-from-iek.md) | Boundary briefing for IEK re-discover signals |

## Boundary Contracts

- **Upstream:** External inputs (board direction, market data, IEK feedback). No formal AIEOS upstream contract — SDK is the pipeline entry point.
- **Downstream:** Frozen PPR hands off above-the-line SBRs to PIK as strategic context for discovery.
- **Feedback:** IEK `re-discover` signals may trigger new SBRs. See [entry-from-iek.md](entry-from-iek.md).
