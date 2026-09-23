# Blueprint Skills

Open skills for product leaders working with AI tools like Claude Code. They turn a product brief into a reviewable spec, help you think through who the product affects and what could go wrong, and keep your project easy to pick back up.

You don't need to write code to use them. Claude does the file handling; you make the product decisions.

## The skills

| Skill | What it does | Creates or updates |
|---|---|---|
| `spec-interview` | Interviews you about your brief, one question at a time, and drafts a bounded, testable spec. Sets up a project folder for you if you don't have one yet. | `SPEC.md` |
| `risk-assessment` | Works through who your product affects and what could go wrong, checks for overlooked risks, helps you score and rank them, plans how to handle the top ones, and proposes new requirements for your spec. | `STAKEHOLDER-REGISTER.md`, `RISK-REGISTER.md`, `risk-register.csv`, and approved changes to `SPEC.md` |
| `data-plan` | Works out where each answer your product gives comes from: a query over your tables, retrieval over documents, or a query the model writes. Designs your tables in plain language from your spec's workflows, documents your document set, sets a quality bar, and writes three testable acceptance criteria. | A data-plan section in `SPEC.md`, and optionally a draft `schema/draft-schema.sql` |
| `golden-set` | Writes your first five test cases with you, carrying across the evaluation notes already sitting in your risk register, and records what an acceptable answer looks like before anything is measured. | `EVALS.md`, and approved changes to `SPEC.md` |
| `wrap` | Saves where your project stands so the next session can continue from files, not chat history. | `PROJECT-STATE.md` |
| `resume-project` | Reads your saved project state and recommends the next step, without changing anything. | Nothing |

Every skill tells you what it plans to write and waits for your yes.

## The working system

1. **One folder per project.** Keep each project's brief, spec, and registers together in its own folder, for example `~/projects/my-capstone/`. Open that folder in Claude Code whenever you work on the project. You don't have to create it yourself; `spec-interview` offers to set it up.
2. **`/wrap` before you stop.** Run it at the end of a session, or before you clear a long conversation with `/clear`.
3. **`/resume-project` when you come back.** Open the project folder, run it, and approve the next step.

## Install

### Option A: ask Claude to install them (recommended)

Open Claude Code and paste this message:

```text
Install the skills from https://github.com/aicareerboost/blueprint-skills into my personal Claude skills folder (~/.claude/skills). Copy each folder inside skills/ as its own skill. If a skill with the same name already exists, ask me before replacing it. Then list what you installed.
```

Claude downloads the skills and copies them into place. Start a new session, then type `/` to see them in the menu. Commands: `/spec-interview`, `/risk-assessment`, `/data-plan`, `/golden-set`, `/wrap`, `/resume-project`.

### Option B: install as a plugin

In Claude Code, run:

```text
/plugin marketplace add aicareerboost/blueprint-skills
/plugin install blueprint@aicareerboost
```

Plugin skills carry a prefix: `/blueprint:spec-interview`, `/blueprint:risk-assessment`, `/blueprint:data-plan`, `/blueprint:golden-set`, `/blueprint:wrap`, `/blueprint:resume-project`.

## Use them in order

1. Open Claude Code and run `/spec-interview`. Point it to your brief: a file, pasted text, or the contents of a Google Doc. It sets up your project folder if needed, interviews you, and writes `SPEC.md` after you approve.
2. In the same project folder, run `/risk-assessment`. It builds your stakeholder and risk registers with you and proposes requirements for `SPEC.md`.
3. Run `/data-plan` then `/golden-set`. The first adds a data plan to `SPEC.md`; the second writes your first five test cases from it and your risk register.
4. Run `/wrap` before you finish. Next time, open the folder and run `/resume-project`.

Want feedback? Share your spec or registers in your cohort channel or `#share-your-work`.

## Privacy and safety

- Review any skill before you install it. These are plain text files; you can read every instruction.
- Keep confidential company information, customer data, credentials, and material you aren't authorized to share out of your project folder.
- The skills never send messages, publish, or connect to outside services. They write only the files listed above, after asking.
- The risk skill surfaces legal, privacy, and security questions for qualified review. It does not give legal advice.

## Method

`spec-interview` uses a requirements-first clarification loop: establish evidence, ask one consequential question at a time, get product-owner decisions, draft only after approval, and audit the result before technical planning. Its design draws on established specification practices, including [GitHub Spec Kit's separation of specification, clarification, planning, and implementation](https://github.com/github/spec-kit/blob/main/docs/reference/agentic-sdd.md), [structured observable requirements](https://www.incose.org/wp-content/uploads/2026/01/INCOSEContent-411.pdf), and [Given/When/Then acceptance examples](https://cucumber.io/docs/gherkin/reference/).

`risk-assessment` follows a lightweight practice: a stakeholder impact assessment, a living risk register scored by likelihood and severity, a gap check against three layers of AI product risk (product and organization, LLM behavior, and agency), and a complete plan for each priority risk: mitigation, contingency, detection, guardrail, owner, and review trigger.

## License

MIT. See [LICENSE](LICENSE).
