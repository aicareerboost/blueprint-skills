# Risk register template

Write `RISK-REGISTER.md` in this shape, and write `risk-register.csv` with the same columns and rows as the table. Keep it plain.

```markdown
# Risk register: <product name>

- Last updated: <YYYY-MM-DD>
- Source: SPEC.md <version>, STAKEHOLDER-REGISTER.md
- Scoring: likelihood (1-3) x severity (1-3) = score (1-9)
- The line: <for example, score 6 or higher>
- Review cadence: <for example, weekly during build, and after any incident or model change>

## Register

Sorted by score, highest first.

| ID | Risk scenario | Layer | Affected stakeholders | Likelihood | Severity | Score | Above the line | Mitigation (before) | Contingency (after) | Detection or evaluation | Guardrail or approval boundary | Owner | Review trigger | Linked requirements | Status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RISK-01 | When <condition>, <failure> may cause <consequence>. | Product / LLM / Agency | | 1-3 | 1-3 | 1-9 | Yes / No | | | | | | | REQ-xx | Open / Planned / Monitoring / Closed |

## Questions for qualified review

- <legal, privacy, security, or IP question>

## Update log

- <YYYY-MM-DD>: <what changed>
```

## CSV header

Use this exact header row in `risk-register.csv`:

```text
ID,Risk scenario,Layer,Affected stakeholders,Likelihood,Severity,Score,Above the line,Mitigation (before),Contingency (after),Detection or evaluation,Guardrail or approval boundary,Owner,Review trigger,Linked requirements,Status
```

For risks below the line, leave the planning columns blank or write "Not yet planned".
