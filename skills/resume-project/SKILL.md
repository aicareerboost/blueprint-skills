---
name: resume-project
description: Pick up a project from its files after a break or a cleared conversation. Reads PROJECT-STATE.md and the files it points to, reports where things stand, and recommends one next action without changing anything.
disable-model-invocation: true
---

# Resume the current project

Rebuild the picture of the project from files on disk, then stop and ask before doing any work. This is part of a simple working system: **one folder per project**, `/wrap` before you stop or clear, and `/resume-project` when you come back.

The people using this skill are often product leaders, not developers. Use plain language and keep the pickup brief short.

## Steps

1. **Confirm the project folder.** State the current folder in one sentence and treat it as the project boundary. If it does not look like a project folder, ask which folder to use. Do not search the rest of the computer.
2. **Find the handoff.** Look for `PROJECT-STATE.md`.
   - If it exists, continue.
   - If it does not, say there is no saved handoff yet. Offer a quick look at the files in this folder, and suggest running `/wrap` at the end of this session so next time is faster.
3. **Read in the "Start here" order** listed in `PROJECT-STATE.md`, and only as much as you need to confirm the current state.
4. **Check for conflicts** between `CLAUDE.md`, `PROJECT-STATE.md`, the brief, `SPEC.md`, and any registers. Prefer explicit dated decisions over inference, and flag every conflict for the user.
5. **Give a short pickup brief:**
   - current goal and status;
   - what is already done;
   - the latest decisions, with the file that supports each;
   - constraints and risks to keep in mind;
   - open questions;
   - anything that looks stale or uncertain; and
   - one recommended next action.
6. **Stop and ask** whether to go ahead with that action or do something else.

## Safety boundaries

- Do not edit files, run external actions, install tools, connect services, send messages, commit, deploy, or publish.
- Do not fill gaps from general knowledge or from an earlier conversation. If something is not in the files, say so.
- Name the file behind each important statement.
