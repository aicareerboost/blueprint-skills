# AI product risk taxonomy

Use this taxonomy for the gap check. The three layers overlap. A single risk can touch more than one layer; record it once and note the layers it touches.

## Layer 1: Product and organization

These risks exist even without a language model. AI gives them new forms.

| Category | Questions to ask |
|---|---|
| Use-case fit | Is AI the right tool for this job? What happens when the model's capabilities fall short? |
| Stakeholder harm | Who could be worse off, including people who never chose the product? |
| Privacy and data rights | What personal or sensitive data enters, persists, or leaves? Was it collected with the right permission? Can it be deleted on request? |
| Security | Who can reach the data, prompts, logs, and outputs? What happens if they leak? |
| Bias and accessibility | Could some groups get worse results or be excluded? |
| Legal, regulatory, IP, and copyright | Which rules might apply where the product is used? Do we have rights to the content we use and generate? These are questions for qualified review, not conclusions. |
| Reliability | What happens when the system is slow, down, or wrong? |
| Cost | Could usage or model costs grow faster than value? |
| Reputation | What output or behavior would embarrass the organization? |
| Ownership | Who is accountable for the product's decisions, errors, and complaints? |

## Layer 2: LLM behavior

These come from generated language.

| Category | Questions to ask |
|---|---|
| Unsupported claims (hallucination) | Could the model state something false with confidence? Who would act on it? |
| Variability (non-determinism) | Could the same input produce different answers? Is that acceptable here? |
| Weak provenance | Can users see where an answer came from? |
| Stale knowledge | Could answers rely on outdated information? |
| Leakage | Could the model reveal private data, prompts, or other users' information? |
| Over-reliance | Could people stop checking outputs they should verify? |
| Policy evasion | Could users talk the model into unsafe or off-limits behavior? |

## Layer 3: Agency

These appear when the system can access data, use tools, keep memory, or take actions. Skip this layer only if the product can do none of these.

| Category | Questions to ask |
|---|---|
| Excessive permission scope | Does the system have more access than the task requires? |
| Tool misuse and confused identity | Could it use a tool incorrectly, or act with the wrong person's authority? |
| Prompt injection and poisoned memory or context | Could untrusted content (a web page, email, or document) carry instructions the system follows, or plant something in its memory? |
| Cascading actions | Could one wrong step trigger others across systems? |
| Irreversible actions | Can it send messages, make purchases, publish, delete, or change records that are hard to undo? |
| Uncontrolled loops and cost | Could it repeat work, talk to other agents without stopping, or run up a bill? |
