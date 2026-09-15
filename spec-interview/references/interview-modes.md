# Interview modes

Read this reference before interviewing. Use the lightest mode that resolves consequential uncertainty.

## Coverage map

Privately classify each area as `Clear`, `Partial`, or `Missing` and cite the supporting source where available:

- intended outcome and evidence the problem matters;
- primary user and affected stakeholders;
- scope, non-goals, and deferred ideas;
- critical workflow and important edge cases;
- success and acceptance evidence;
- failure, refusal, recovery, and human approval;
- data, integrations, permissions, and provenance;
- product, organizational, LLM, agentic, privacy, security, legal, contractual, and intellectual-property risks;
- constraints and dependencies; and
- unresolved decisions.

Do not show the full map unless it helps the owner review the reasoning. Use it to select the smallest set of questions that can change the spec materially.

## Assumption review

Use this mode when briefs, research, prototypes, or prior decisions support a useful first interpretation.

For each consequential assumption, show:

```text
ASSUMPTION: <concise interpretation>
EVIDENCE: <source path, section, or owner decision>
IF WRONG: <decision, requirement, evaluation, or risk that changes>
```

Group related assumptions and ask the owner to correct what is wrong or incomplete. Do not ask them to reconfirm every supported fact. Convert corrections into decisions, assumptions to validate, or open questions before drafting.

## Clarification interview

Ask exactly one question at a time. Rank candidate questions by:

1. **Impact** — how much the answer changes scope, behavior, evaluation, or risk;
2. **Uncertainty** — how weak or conflicting the current evidence is; and
3. **Irreversibility** — how costly or consequential a wrong choice would be.

Explain in one sentence why the question matters. Offer a short set of distinct options only when that makes the decision easier without steering the owner. Accept no more than five answers per pass. Preserve lower-priority gaps as assumptions or stable-ID open questions for a later pass.

## Delta update

Use this mode when a canonical spec exists:

1. Read the canonical spec, its sources, and recorded decisions.
2. Identify only the changes supported by new evidence or owner direction.
3. Present `ADDED`, `MODIFIED`, `REMOVED`, and `DEFERRED` items with rationale and downstream impact.
4. Wait for explicit approval before changing the canonical file.
5. Retain an existing stable ID when its meaning remains substantially the same; assign a new ID when it represents a new obligation, risk, decision, or question.
6. Append a concise dated record of the accepted clarification or decision.

Do not introduce a planning pipeline, engineering task tree, framework CLI, branch convention, or automatic implementation handoff.
