---
name: wrap
description: Save a short, durable handoff for the current project to PROJECT-STATE.md in the project folder, so the next session can pick up from files instead of chat history. Run it before ending a session or clearing the conversation.
disable-model-invocation: true
---

# Wrap the current project

Save where the project stands in `PROJECT-STATE.md`, so a fresh session can continue from the files. This is part of a simple working system: **one folder per project**, `/wrap` before you stop or clear, and `/resume-project` when you come back.

The people using this skill are often product leaders, not developers. Explain what you are doing in plain language and never ask them to create files or folders by hand.

## Steps

1. **Confirm the project folder.** State the current folder in one sentence and treat it as the project boundary. If it does not look like a project folder (no brief, spec, or project files), say so and ask which folder the project lives in before writing anything.
2. **Gather only what you need.** Review this conversation and the few files that verify the current state, in this order when they exist: `CLAUDE.md`, `PROJECT-STATE.md`, the brief, `SPEC.md`, `STAKEHOLDER-REGISTER.md`, `RISK-REGISTER.md`. Do not scan other folders.
3. **Draft the handoff** using [references/project-state-template.md](references/project-state-template.md). Record:
   - the current goal and status;
   - what was completed this session;
   - decisions made, why, and the file that shows each one;
   - the current files and what each is for;
   - constraints and risks that must carry forward;
   - open questions; and
   - one concrete next action, plus anything the next session should not do.
4. **Keep uncertainty visible.** Leave unresolved matters as open questions. Do not turn guesses into decisions.
5. **Add a "Start here" reading order** so a fresh session loads the fewest files needed.
6. **Keep the update log short.** Add today's date and time with a one-line summary, and keep only the five most recent entries.
7. **Ask before writing.** Say that only `PROJECT-STATE.md` will be created or updated, summarize what it will record, and wait for a yes. If the file exists, update it rather than starting over.
8. **Check the result.** Re-read the file and point out anything missing or contradictory.
9. **Close with the next move:** "You can now clear this conversation with `/clear` or end the session. Next time, open this project folder and run `/resume-project`."

## Safety boundaries

- Do not edit any file other than `PROJECT-STATE.md`.
- Do not include passwords, API keys, access tokens, or confidential details. Describe them in general terms instead.
- Do not run external actions, install tools, connect services, send messages, commit, deploy, or publish.
- The handoff records project facts, decisions, evidence, and next actions. It is not a transcript of the conversation.
