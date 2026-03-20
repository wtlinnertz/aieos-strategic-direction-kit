# Strategic Direction Kit — Playbook

This playbook defines the end-to-end process for capturing strategic bets and prioritizing them into a funded portfolio that feeds the Product Intelligence Kit. It is the authoritative process definition for the Strategic Direction Kit.

---

## Artifact Flow

The Strategic Direction Kit produces five artifact types in two phases. The Roadmap Phase catalogs existing capabilities and plans future direction. The Bet Phase extracts and prioritizes individual strategic bets.

```
External Inputs (board direction, market data, IEK feedback, customer signals)
        │
        ├──── Roadmap Ideation Workshop (optional utility prompt)
        │
        ▼
┌─────────────────────────┐
│  Capability Lifecycle   │  Step 1: Catalog existing capabilities
│  Assessment (CLA)       │  author → validate → freeze
└────────┬────────────────┘
         ▼
┌─────────────────────────┐
│  Product Capability     │  Step 2: Define product roadmap
│  Roadmap (PCR)          │  generate → validate → freeze
└────────┬────────────────┘
         ▼
┌─────────────────────────┐
│  Technology Investment   │  Step 3: Define technology roadmap
│  Roadmap (TIR)          │  generate → validate → freeze
└────────┬────────────────┘
         │ PCR "committed" entries become bet candidates
         ▼
┌─────────────────────────┐
│  Strategic Bet Record   │  Step 4: Capture a single bet (per theme)
│  (SBR)                  │  author → validate → freeze
└────────┬────────────────┘
         │ (repeat for each bet)
         ▼
┌─────────────────────────┐
│  Portfolio               │  Step 5: Rank all active bets
│  Prioritization Record  │  author → validate → freeze
│  (PPR)                  │
└────────┬────────────────┘
         │ above-the-line SBRs
         ▼
   Handoff to Product
   Intelligence Kit (PIK)
```

**Retroactive onboarding:** For existing products entering AIEOS for the first time, start at Step 1 (CLA). You don't need prior AIEOS artifacts — CLA accepts informal inputs (product wiki, feature lists, team knowledge). The CLA catalogs what exists, then PCR and TIR plan what comes next.

**Skipping the Roadmap Phase:** If you already have a concrete bet to evaluate (not derived from roadmap planning), skip directly to Step 4 (SBR). The Roadmap Phase is for organizations planning their portfolio direction, not for individual bets that arrive ad hoc.

---

## Utility Prompts

### Roadmap Ideation Workshop

**Prompt:** `aieos-product-intelligence-kit/docs/prompts/ideation-workshop-prompt.md` (§Roadmap-Level Ideation)

**When to use:** Before Step 1 (CLA), when the team needs help imagining the product or technology direction. Uses 7 roadmap-specific techniques (Future-Back Planning, Capability Gap Mapping, Technology Horizon Scan, Competitive Trajectory, Sunset Analysis, Customer Journey Evolution, Platform Leverage Analysis).

**Output:** Roadmap Ideation Record (`docs/sdlc/00-roadmap-ideation.md`) — feeds directly into CLA and PCR creation.

**No AIEOS history required:** 6 of 7 techniques work without prior initiatives.

---

## Phase 1: Roadmap

### Step 1: Capability Lifecycle Assessment (CLA)

**Artifact ID format:** `CLA-{PRODUCT}-{NNN}`

**Inputs:**
- User-provided capability list (REQUIRED — AI must not invent capabilities)
- `docs/principles/strategic-direction-principles.md` (organizational policy)
- Optional: IEK ES files, RRK RHR files, existing product documentation
- Optional: Roadmap Ideation Record (if roadmap ideation was run)

**Generation:**
- Use `docs/prompts/cla-prompt.md` in a dedicated AI session
- The prompt references `docs/specs/cla-spec.md` for content rules
- The prompt references `docs/artifacts/cla-template.md` for structure
- The AI structures and assesses the user's capability list — it does not invent capabilities
- For retroactive onboarding: accept informal inputs (wiki pages, feature lists, dashboards)

**Validation:**
- In a **separate AI session**, use `docs/validators/cla-validator.md`
- All 6 hard gates must PASS (including `user_provided_inventory`)

**Freeze:**
- The product/portfolio owner reviews the validated CLA
- The owner approves the freeze
- The CLA is now eligible as input to PCR

**Lifecycle:** Living document. Re-frozen semi-annually, when IEK produces new ES signals, or when material changes occur. Version increments (v1, v2, v3).

---

### Step 2: Product Capability Roadmap (PCR)

**Artifact ID format:** `PCR-{PRODUCT}-{NNN}`

**Precondition:** Frozen CLA exists.

**Inputs:**
- Frozen CLA (required)
- Roadmap Ideation Record (optional — if roadmap ideation was run)
- `docs/principles/strategic-direction-principles.md`

**Generation:**
- Use `docs/prompts/pcr-prompt.md` in a dedicated AI session
- Every capability must trace to a CLA entry or a documented new opportunity
- Capabilities must not be invented without a source

**Validation:**
- In a **separate AI session**, use `docs/validators/pcr-validator.md`
- All 6 hard gates must PASS (including `capacity_realistic`)

**Freeze:**
- The portfolio owner reviews the validated PCR
- The owner approves the freeze
- "Committed" entries are eligible for SBR extraction

**Lifecycle:** Re-frozen quarterly during planning cycles.

---

### Step 3: Technology Investment Roadmap (TIR)

**Artifact ID format:** `TIR-{PRODUCT}-{NNN}`

**Precondition:** Frozen PCR exists.

**Inputs:**
- Frozen PCR (required)
- Frozen CLA (recommended)
- Current technology stack documentation
- `docs/principles/strategic-direction-principles.md`
- Optional: PINFK PDRs (if any)

**Generation:**
- Use `docs/prompts/tir-prompt.md` in a dedicated AI session
- Every investment must trace to a PCR capability or operational need
- Technology for technology's sake fails the `driver_traced` gate

**Validation:**
- In a **separate AI session**, use `docs/validators/tir-validator.md`
- All 5 hard gates must PASS

**Freeze:**
- The technology owner reviews the validated TIR
- The owner approves the freeze

**Lifecycle:** Re-frozen annually or when PCR material changes require technology reassessment.

---

## Phase 2: Strategic Bets

### Step 4: Strategic Bet Record (SBR)

**Artifact ID format:** `SBR-{THEME}-{NNN}`

**Inputs:**
- Executive sponsor's strategic intent (informal — conversation, brief, slide, directive)
- `docs/principles/strategic-direction-principles.md` (organizational policy)
- Optional: IEK Evolution Signal (if triggered by a re-discover signal)

**Generation:**
- Use `docs/prompts/sbr-prompt.md` in a dedicated AI session
- The prompt references `docs/specs/sbr-spec.md` for content rules
- The prompt references `docs/artifacts/sbr-template.md` for structure
- The AI helps the sponsor structure their thinking — it does not generate strategy
- If the sponsor's input cannot produce a falsifiable thesis, the prompt asks clarifying questions rather than fabricating one

**Validation:**
- In a **separate AI session**, use `docs/validators/sbr-validator.md`
- The validator references `docs/specs/sbr-spec.md` for hard gates
- All 6 hard gates must PASS

**Freeze:**
- The executive sponsor reviews the validated SBR
- The sponsor approves the freeze
- The SBR is now eligible for inclusion in a PPR

**Expiration:**
- Unreferenced SBRs (not in any frozen PPR) expire 180 days after freeze
- Active SBRs (in a frozen PPR) are governed by their time horizon
- Expired SBRs transition to Abandoned status

---

### Step 5: Portfolio Prioritization Record (PPR)

**Artifact ID format:** `PPR-{NNN}`

**Precondition:** At least 2 frozen SBRs exist.

**Inputs:**
- All non-expired, non-abandoned frozen SBRs
- Available capacity (teams, budget, time)
- Portfolio owner's preliminary ranking or priorities
- `docs/principles/strategic-direction-principles.md` (organizational policy)
- Optional: Prior frozen PPR (for change context)
- Optional: IEK Evolution Signals or Portfolio Evolution Signals

**Generation:**
- Use `docs/prompts/ppr-prompt.md` in a dedicated AI session
- The prompt references `docs/specs/ppr-spec.md` for content rules
- The prompt references `docs/artifacts/ppr-template.md` for structure
- The AI surfaces trade-offs and tests consistency — the portfolio owner decides the ranking

**Validation:**
- In a **separate AI session**, use `docs/validators/ppr-validator.md`
- All 5 hard gates must PASS

**Freeze:**
- The portfolio owner reviews the validated PPR
- The portfolio owner approves the freeze
- Above-the-line SBRs are now funded and may be routed to PIK

---

## Downstream Handoff

### Delivery to PIK

Above-the-line SBRs from the frozen PPR are routed to the Product Intelligence Kit as strategic context for discovery.

**Handoff mechanism:** When initiating a PIK Discovery Intake, reference the frozen PPR line item and the corresponding frozen SBR. The SBR's thesis, success signal, and failure signal become strategic context inputs for the Discovery Intake Form.

**No regeneration:** The SBR and PPR are not re-processed by PIK. They are reference artifacts — PIK's Discovery Intake structures the discovery engagement, not the strategic bet.

### PIK Dependencies on SDK Artifacts

PIK may reference these sections of the frozen SBR:
- §2 Thesis — what the organization is betting on
- §3 Success Signal — how the bet's success will be measured
- §4 Failure Signal — what would cause the bet to be abandoned
- §6 Investment Envelope — rough resource scope

PIK may reference these sections of the frozen PPR:
- §3 Ranked Bet List — priority position of the funded bet
- §5 Capacity Allocation — resource allocation for the bet

### When SDK Artifacts Are Optional

Not all PIK engagements require SDK artifacts. SDK is the entry point for **new strategic bets**. These existing flows bypass SDK:

- **Enhancement (Preset 2):** Scope is understood; enters EEK directly via Path B
- **Incident-triggered fix (Preset 4):** Enters via ODK or RRK, routes to EEK
- **IEK re-discover within existing bet scope:** Can route directly to PIK if the bet already exists and is active
- **Operational refinements:** Do not require strategic re-evaluation

SDK becomes relevant when the organization is deciding **what new things to invest in**, not when refining or fixing existing investments.

---

## Upstream Interface

### IEK Feedback Loop

The Insight & Evolution Kit (Layer 7) may produce a `re-discover` signal indicating that a service or capability warrants strategic re-evaluation. When this occurs:

1. A human product owner reviews the IEK Evolution Signal
2. The product owner decides: is this a **new strategic question** (route to SDK for a new SBR) or a **refinement within an existing bet** (route to PIK directly)?
3. If routed to SDK: create a new SBR citing the ES artifact ID in §7 Strategic Context
4. If routed to PIK: the existing SBR and PPR remain unchanged; PIK handles the re-discovery

This keeps SDK lean — it gates new investments, not operational feedback loops.

### External Inputs

SDK accepts external inputs informally: board directives, market signals, customer data, competitive intelligence. These are not AIEOS artifacts. The SBR structures them into a governed format.

---

## Freeze Points

| Artifact | Freeze Point | What It Unlocks |
|----------|-------------|-----------------|
| CLA | After validation PASS + owner approval | PCR generation |
| PCR | After validation PASS + owner approval | TIR generation + SBR extraction |
| TIR | After validation PASS + owner approval | PINFK alignment + technology planning |
| SBR | After validation PASS + sponsor approval | Eligibility for PPR inclusion |
| PPR | After validation PASS + portfolio owner approval | Handoff of above-the-line bets to PIK |

---

## Re-Entry Protocol

### SBR Re-Entry

When a frozen SBR must change (e.g., thesis invalidated, signals revised, time horizon extended):

1. **Impact analysis** — Determine if the SBR is referenced in a frozen PPR. If yes, the PPR is affected.
2. **Modify** — Update the SBR in a new AI session.
3. **Re-validate** — All 6 hard gates must PASS.
4. **Sponsor approval** — The executive sponsor approves the re-freeze.
5. **PPR cascade** — If the SBR is referenced in a frozen PPR, the PPR must be re-validated. If the change affects ranking (e.g., investment envelope changed), the PPR may need regeneration.

### PPR Re-Entry

When a frozen PPR must change (e.g., capacity changed, new SBR created, bet abandoned):

1. **Modify** — Update the PPR in a new AI session with updated SBR inventory.
2. **Re-validate** — All 5 hard gates must PASS.
3. **Portfolio owner approval** — The portfolio owner approves the re-freeze.
4. **PIK notification** — If above-the-line bets changed, notify PIK teams. Active discovery engagements referencing a now-below-the-line bet must be assessed for continuation or suspension.

---

## Iteration Rules

### Within a Step

If validation fails:
1. Review the blocking issues in the validator output
2. Regenerate or revise the artifact in a **new AI session** with the validator feedback
3. Re-validate in a **separate AI session**
4. Repeat until all hard gates PASS

### SBR Quality Indicators

Common validation failures and their root causes:
- `thesis_falsifiable` FAIL → the sponsor's input is aspirational, not testable. Ask "what evidence would prove this wrong?"
- `failure_signal_defined` FAIL → the sponsor has not considered what would cause abandonment. This is the hardest conversation but the most valuable.
- `single_accountable_owner` FAIL → committee ownership was specified. Ask "who would we call if this bet needs a decision at 2am?"

---

## Maintaining the Engagement Record

The Engagement Record (ER) is a project-level artifact that lives in the consuming project at `docs/engagement/er-{initiative}.md`. It spans all AIEOS layers and is maintained by each kit's operators as work passes through.

**SDK maintains the Layer 1 section of the ER.**

### When to Update the ER

| Trigger | ER update |
|---------|-----------|
| CLA frozen/revised | Add CLA ID + version to §1a artifact table |
| PCR frozen/revised | Add PCR ID + version to §1a; note horizon |
| TIR frozen/revised | Add TIR ID + version to §1a; note horizon |
| SBR frozen | Add SBR ID to §1a artifact table |
| PPR frozen | Add PPR ID to §1a; record above/below-the-line status |
| SBR expired or abandoned | Update §1a status |

---

## Session Discipline

- **One artifact per generation session** — do not generate SBR and PPR in the same session
- **Separate generation and validation sessions** — prevents self-validation bias
- **Include the spec, prompt, and template** for generation sessions
- **Include the spec and validator** for validation sessions
- **Include all frozen SBRs** when generating a PPR — do not summarize
