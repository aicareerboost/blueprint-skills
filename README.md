# Blueprint Skills

Open, reusable agent skills for product leaders working with AI-enabled development tools.

## Available skills

### `spec-interview`

Interviews a product owner and turns an existing brief, prototype, or idea into a bounded, testable, risk-aware product specification. It explicitly separates evidence, decisions, assumptions, and open questions, and it prevents the agent from rushing from an underspecified idea into implementation.

The workflow is designed for product discovery and early specification. It does not require coding.

## Install in a Claude Code project

Copy the complete skill directory into the project:

```text
your-project/
└── .claude/
    └── skills/
        └── spec-interview/
            ├── SKILL.md
            └── references/
                └── spec-template.md
```

Start Claude Code from the project root and invoke:

```text
/spec-interview
```

Place the relevant brief, research, or prototype notes in the project or tell Claude which files to use. The skill will interview you before proposing or writing a specification.

Review downloaded skills before using them. Keep confidential data, credentials, and material you are not authorized to process out of the project.

## Method

The skill uses a requirements-first clarification loop: establish evidence, ask one consequential question at a time, obtain product-owner decisions, draft only after approval, and audit the result before technical planning.

Its design is informed by established specification practices, including [GitHub Spec Kit's separation of specification, clarification, planning, and implementation](https://github.com/github/spec-kit/blob/main/docs/reference/agentic-sdd.md), [structured observable requirements](https://www.incose.org/wp-content/uploads/2026/01/INCOSEContent-411.pdf), and [Given/When/Then acceptance examples](https://cucumber.io/docs/gherkin/reference/).
