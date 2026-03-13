# Strategic Direction Kit — Tests

Structural integrity is verified by the governance foundation's `check-structure.sh` script:

```bash
aieos-governance-foundation/tests/check-structure.sh ./aieos-strategic-direction-kit
```

This checks:
- Required files and directories exist
- Four-file completeness (every spec has a template, prompt, and validator)
- Naming conventions
- Governance model sync with foundation
