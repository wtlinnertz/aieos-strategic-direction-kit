# How to Use the Strategic Direction Kit with AI

This guide explains how to use AI assistants (e.g., Claude Code) to author and validate SDK artifacts.

---

## Overview

Unlike downstream kits where AI generates artifacts from frozen inputs, SDK artifacts are **human-authored with AI assistance**. The executive sponsor owns the strategic thinking. The AI helps structure it into a governed format and validates it against hard gates.

## Session Types

### SBR Authoring Session

**Setup:**
1. Load `docs/prompts/sbr-prompt.md`
2. Load `docs/specs/sbr-spec.md`
3. Load `docs/artifacts/sbr-template.md`
4. Load `docs/principles/strategic-direction-principles.md`
5. Optional: load IEK Evolution Signal if this bet is triggered by a re-discover signal

**What to expect:** The AI will ask the sponsor clarifying questions to produce a falsifiable thesis. If the sponsor's input is too vague, the AI will say so rather than fabricate a thesis. Expect pushback on:
- Aspirational statements that aren't falsifiable
- Missing failure signals
- Unbounded time horizons or investment envelopes
- Committee ownership

### SBR Validation Session

**Setup (separate session):**
1. Load `docs/validators/sbr-validator.md`
2. Load `docs/specs/sbr-spec.md`
3. Load the draft SBR

**What to expect:** PASS/FAIL judgment on 6 hard gates. No suggestions, no redesign.

### PPR Authoring Session

**Setup:**
1. Load `docs/prompts/ppr-prompt.md`
2. Load `docs/specs/ppr-spec.md`
3. Load `docs/artifacts/ppr-template.md`
4. Load `docs/principles/strategic-direction-principles.md`
5. Load all frozen SBRs (complete — do not summarize)
6. Load available capacity information

**What to expect:** The AI will surface trade-offs and test the consistency of the ranking. It will push back on ties, over-commitment, and vague rationale. The portfolio owner makes the ranking decisions.

### PPR Validation Session

**Setup (separate session):**
1. Load `docs/validators/ppr-validator.md`
2. Load `docs/specs/ppr-spec.md`
3. Load the draft PPR

**What to expect:** PASS/FAIL judgment on 5 hard gates. No suggestions, no redesign.

## Tips

- **Start with the failure signal.** When authoring an SBR, start with §4 (Failure Signal) before §2 (Thesis). If the sponsor can't articulate what would cause abandonment, the bet isn't ready.
- **Bring real numbers.** Success and failure signals need specific metrics. "Improve retention" is not measurable. "Reduce 30-day churn from 12% to 8%" is.
- **Don't fight the rank order.** The PPR validator will fail ties. If two bets feel equal, ask: "If we could only fund one, which one?" That's the ranking.
