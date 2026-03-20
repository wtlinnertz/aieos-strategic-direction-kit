# Technology Investment Roadmap

## §1 Document Control

| Field | Value |
|-------|-------|
| Artifact ID | TIR-{SCOPE}-{NNN} |
| Status | Draft / Validated / Freeze Pending / Frozen |
| Author | {name} |
| Technology Owner | {single named individual} |
| Date | {YYYY-MM-DD} |
| Horizon | {2-5yr} |
| Governance Model Version | {from governance-model.md §15} |
| Spec Version | {from tir-spec.md} |
| Principles Version | {from strategic-direction-principles.md} |

## §2 Technology Landscape

| Area | Current State | Target State | Classification | Driver | Investment Level | Timeframe |
|------|--------------|-------------|----------------|--------|-----------------|-----------|
| {technology area} | {what is in place today} | {desired future state} | {adopt / hold / retire} | {PCR capability ref or operational need} | {major / moderate / minor} | {quarter/half/year} |

## §3 Adoption Plans

{One entry per "adopt" classification in §2. If no adoptions, state "No adoption plans — all technologies are hold or retire."}

### {Technology Area — Adopt}

**Evaluation Criteria:**
- {measurable criterion 1}
- {measurable criterion 2}

**POC Plan:**
| Field | Value |
|-------|-------|
| Scope | {what the POC covers} |
| Timeline | {bounded duration} |
| Success Criteria | {measurable outcomes that determine POC success} |

**Rollout Timeline:**
| Phase | Milestone | Target Date |
|-------|----------|-------------|
| {phase name} | {milestone description} | {date or timeframe} |

## §4 Retirement Plans

{One entry per "retire" classification in §2. If no retirements, state "No retirement plans — all technologies are hold or adopt."}

### {Technology Area — Retire}

**Migration Path:**
{What replaces this technology and how the migration will be executed.}

**Timeline:**
| Phase | Description | Target Date |
|-------|------------|-------------|
| {phase name} | {what happens in this phase} | {date or timeframe} |

**Affected Systems:**
| System | Dependency Type | Migration Impact |
|--------|----------------|-----------------|
| {system name} | {how it depends on the retiring technology} | {what changes for this system} |

**Risk Assessment:**
| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| {risk description} | {high/medium/low} | {high/medium/low} | {mitigation approach} |

## §5 PCR Alignment

### TIR to PCR Mapping

| TIR Technology (Adopt) | PCR Capabilities Enabled |
|------------------------|-------------------------|
| {technology area} | {PCR capability references from PCR §3} |

### PCR to TIR Mapping

| PCR Capability (with Technology Dependency) | TIR Entry |
|---------------------------------------------|-----------|
| {PCR capability reference} | {TIR technology area from §2} |

### Alignment Gaps

{If gaps exist in either direction, describe each gap and its justification. If no gaps, state "No alignment gaps identified — all adopt technologies map to PCR capabilities and all PCR technology dependencies have TIR entries."}
