# CLAUDE.md — Strategic Direction Kit

## What This Repository Is

This is the **Strategic Direction Kit** — an AIEOS kit that governs how an organization captures, validates, and prioritizes strategic bets. It is Layer 1 of the AIEOS system. Its output feeds the Product Intelligence Kit (Layer 2).

## Repository Structure

```
docs/
  principles/          # Organizational strategic direction policy (input material)
  specs/               # Content rules and hard gates per artifact type
  artifacts/           # Templates
  prompts/             # AI-assisted authoring prompts
  validators/          # Quality gate definitions
  playbook.md          # End-to-end process definition
  index.md             # Documentation entry point
  how-to-adapt.md      # Organizational adoption guidance
  how-to-use-with-ai.md # AI tool usage guide
  governance-model.md  # AIEOS structural rules (reference)
  entry-from-iek.md    # Boundary briefing for IEK re-discover signals
examples/              # Worked examples
tests/                 # Structural integrity checks
```

## Artifact Types

This kit produces two artifact types:

1. **Strategic Bet Record (SBR)** — A single falsifiable strategic bet with measurable signals and bounded scope
2. **Portfolio Prioritization Record (PPR)** — A strict-rank-ordered list of active SBRs with trade-off rationale and a capacity cut line

Each artifact type has exactly four governing files: spec, template, prompt, validator.

## Key Rules

- **Specs are the source of truth** — prompts and validators reference specs, never inline rules
- **Validators judge, they do not help** — no suggestions, no redesign
- **Freeze before promote** — SBRs must be frozen before PPR can reference them
- **Separate generation and validation** — different AI sessions to prevent self-validation bias
- **Human-authored with AI assistance** — the AI structures thinking, it does not generate strategy
- **Governance model sync** — `docs/governance-model.md` is a synchronized copy of `aieos-governance-foundation/governance-model.md`. Do not edit the kit copy directly.
- **Engagement Record** — SDK maintains the Layer 1 section of the project's ER.

## Artifact Flow

```
External inputs → SBR (per bet) → validate → freeze
                       ↓
              PPR (ranks all frozen SBRs) → validate → freeze
                       ↓
              Above-the-line SBRs → PIK Discovery Intake
```

## Boundary Contracts

- **Upstream:** External inputs (board direction, market data, IEK feedback). No formal AIEOS upstream contract.
- **Downstream:** Frozen PPR hands off above-the-line SBRs to PIK as strategic context for discovery.
- **Feedback:** IEK `re-discover` signals may trigger new SBRs. See `docs/entry-from-iek.md`.

## File Naming

| Type | Pattern |
|------|---------|
| Spec | `{type}-spec.md` |
| Template | `{type}-template.md` |
| Prompt | `{type}-prompt.md` |
| Validator | `{type}-validator.md` |

## When Working on This Kit

- Read the playbook (`docs/playbook.md`) for the full process definition
- Read the governance model (`docs/governance-model.md`) for structural rules
- Check `docs/how-to-use-with-ai.md` for session setup instructions
- Reference `examples/` for worked examples

## Building or Auditing AIEOS Kits

- `aieos-governance-foundation/docs/kit-structure-standard.md` — compliance checklist
- `aieos-governance-foundation/docs/philosophy.md` — design rationale
- `aieos-governance-foundation/docs/layer-model.md` — layer model and kit registry
