# Data plan template

Use this shape when the project does not supply its own data-plan template. Replace `N` with the section number chosen in Step 1 (if the plan replaces an existing data-questions section, this is that section's number). Keep every heading. Where a part does not apply, say why in one line instead of deleting it.

```markdown
## N. Data plan

### N.1 Where the answers live

| Question a user asks | Answer lives in | Why |
|---|---|---|
| <in the user's words> | a query over our tables / retrieval over documents / a query the model writes | <one line; say "the model picks which one" or "the user's own material, per session" where it applies> |

**Not routed** (omit if none):

- **Fixed text the product always shows:** <what, and where it appears>
- **Questions the product declines:** <which, and the sentence it says>

**Terms the model must use** (only if a question routes to a query the model writes, or the model picks from a fixed list):

- **<term>:** <what it means in the data: which rows count, or, where the model picks from a fixed list, which existing segment, level, or value it selects (never a new band)>. <or OPEN QUESTION>

### N.2 Structured data

The tables this product needs, derived from the workflows in section 4.

| Table | Holds | Who owns it | Breaks if wrong |
|---|---|---|---|
| <name> | <one line> | <person or role, or OPEN QUESTION> | <consequence> |

**How the tables relate**

- <for example: each one_on_one belongs to one manager and one direct report>
- <name any many-to-many link table: for example, finding_evidence links each finding to the evidence items it cites>

**Key fields**

<table name>

| Field | What it means | Required |
|---|---|---|
| <name> | <plain language; any fixed list of values; mark personal data> | Yes / No |

- **Does this already exist somewhere?** <what the spec or the owner said, or OPEN QUESTION>
- **If the model writes queries against this, what may it read?** <per table, or "The model does not query these tables.">
- **What must it never be able to write or delete?** <per table, with linked RISK-xx>
- **Who may see which rows?** <from the spec or stakeholder register, or OPEN QUESTION for when access control is built>

### N.3 The corpus

<If there is no corpus: "No corpus. <reason>." and leave the table empty.>

| Source | Format | Owner | How current | How often it changes |
|---|---|---|---|---|

<If the corpus is the user's own material, supplied each session, add: who supplies it, whether it is kept after the session, and what sensitivity applies.>

- **How does a document get in?** <who adds it, and what happens when nobody does>
- **What happens to a document that is replaced?** <and how a reader can tell which version is current>
- **Anything whose content is an image, a scan, or a slide?** <list by name, or "None">
- **What is out of the corpus on purpose,** and what does the product say when someone asks about it?

### N.4 What good retrieval looks like here

- **Must every answer cite its source?** <Yes, and this is REQ-xx / No, because ...>
- **What does the product say when it cannot find an answer?** "<the exact sentence>" <If it has several kinds of refusal, give the "did not understand" sentence here and point to the requirements that word the others.>
- **Who is allowed to see which documents?** <answer; "everyone" only if deliberate>

<If there is no corpus, keep the "cannot find an answer" sentence, which applies to any product, and mark the other two "Not applicable: no corpus".>

### N.5 Quality bar

- **How accurate does this have to be before you would act on it?** <the owner's number, per kind of question if they chose that>
- **Who judges, and what counts as a pass?** <who, and what "correct" or "relevant" means; OPEN QUESTION if only the owner can judge today>
- **What happens at the failures you accept below that bar?** <product behavior>
- **Which is worse here, a wrong answer or no answer?** <which, and why>

### N.6 Acceptance criteria drawn from this plan

- **REQ-xx — <one observable behavior>.** <In the spec's existing requirement pattern and layout; otherwise GIVEN <context>, WHEN <action>, THEN <observable outcome>.> <Linked RISK-xx, if any.>
- **REQ-xx — ...**
- **REQ-xx — ...**

### N.7 Open questions

- **OQ-xx:** <question, what it affects, and whether it blocks the next step>
```

Notes:

- Continue the spec's existing `OQ-` and `REQ-` numbering. Do not reuse retired IDs.
- Label anything not confirmed by the owner or their files as **ASSUMPTION** or **OPEN QUESTION**.
- A workflow product may rename the first routing column to what it produces (for example, "Output the user gets").
- The `Key fields` block and `How the tables relate` list extend the four-column table rather than replacing it, so a spec that follows a four-column course template still matches it.
