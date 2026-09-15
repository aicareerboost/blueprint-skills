# Product specification template

Use this template only when the project does not supply its own. Omit sections that do not apply; do not populate them with generic filler.

```markdown
# <Product or feature name>

- **Version:** 0.1
- **Status:** Draft for review
- **Owner:** <name or OPEN QUESTION>
- **Updated:** <YYYY-MM-DD>
- **Source artifacts:** <briefs, research, prototypes, decisions>

## 1. Problem and intended outcome

- Problem or opportunity
- Evidence currently available
- Outcome being promised
- Why AI is or is not appropriate

## 2. Users and affected stakeholders

- Primary user
- Buyer, operator, approver, and decision-maker as applicable
- Affected non-users and possible benefits or burdens

## 3. Scope and non-goals

### In scope

### Explicitly out of scope

### Deferred ideas

Capture useful ideas that are intentionally outside the current intent or version. Include the reason for deferral.

## 4. Core workflows

Describe the smallest end-to-end behaviors required for this version.

## 5. Requirements and acceptance criteria

Use stable IDs such as `REQ-01` for priority requirements. Each requirement states one observable behavior and includes at least one scenario. Consequential requirements include both success and an applicable failure, refusal, recovery, or human-handoff scenario.

### REQ-01 — <observable behavior>

<One independently testable obligation.>

**Success scenario**

```text
GIVEN <starting context>
WHEN <event or action>
THEN <observable outcome>
```

**Failure, refusal, recovery, or handoff scenario**

```text
GIVEN <consequential condition>
WHEN <event or action>
THEN <observable safe outcome>
```

## 6. Constraints and dependencies

Record known limits without choosing an implementation prematurely.

## 7. Risk and control register

| ID | Risk scenario and consequence | Evidence or assumption | Mitigation | Contingency or trigger | Owner | Human approval or stop boundary | Future evaluation |
|---|---|---|---|---|---|---|---|
| RISK-01 |  |  |  |  |  |  |  |

## 8. Decisions, assumptions, and open questions

### Decisions

- **DEC-01:** <decision and rationale>

### Assumptions to validate

### Open questions

- **OQ-01:** <question, consequence, and whether it blocks the next decision>

## 9. Data and evidence questions

- Required sources
- Access and permissions
- Quality and representativeness
- Freshness and update cadence
- Provenance and citation
- Retention and privacy

## 10. Next decision

Name the next decision or evidence-gathering step. Do not silently turn it into an implementation task.

## 11. Decision and clarification record

Append concise dated entries when an approved interview pass changes the spec.

| Date | IDs affected | Accepted change and rationale |
|---|---|---|
```
