# Optional draft schema

Read this only when the owner asks for a draft of the database code. The data plan in `SPEC.md` is the design. This file is a preview of how that design becomes a database when the product is built. It is not run in this session.

## Rules

- Draft only the tables in the approved data plan. Do not add tables, fields, or relationships the owner did not approve. If the draft reveals a gap, such as a field the plan forgot, stop and amend the spec first (Step 7, "Amending an approved section").
- Write for Postgres, as used by Supabase.
- **No data.** No `INSERT` statements, no sample rows, and nothing copied from a real system. Real records never go in this file.
- No credentials, connection strings, project URLs, or keys.
- Do not run it, and do not suggest a command that would.

## Shape

Save as `schema/draft-schema.sql` in the project folder, creating `schema/` if needed, after the owner approves the content.

```sql
-- <Product name>: DRAFT schema
--
-- A preview, not run. Generated from the data plan in SPEC.md, section <N>,
-- on <YYYY-MM-DD>. If this file and SPEC.md disagree, SPEC.md is right.
--
-- This becomes a real database when the product is built. Access rules
-- (who may see which rows, what the model may never change) are noted
-- per table so they can become database policies then.

-- <table>: <what it holds, in one line>
-- Owner: <from the plan>. Breaks if wrong: <from the plan>.
-- Access: <what the model may read; what it must never write or delete>.
create table if not exists <table> (
  id          bigint generated always as identity primary key,
  <field>     <type> not null,        -- <what it means, from the plan>
  <field>     <type>,                 -- optional: <what it means>
  <parent>_id bigint not null references <parent> (id),
  created_at  timestamptz not null default now()
);
```

## Conventions

- One comment block per table, in plain language, taken from the plan.
- Required fields in the plan are `not null`. Optional fields are nullable.
- A field with a fixed list of values uses a `check (<field> in (...))` constraint, with the list taken from the plan.
- Each relationship in the plan becomes a `references` line. Create tables in an order where each parent exists before its child.
- A many-to-many link table in the plan gets two `references` columns and a composite primary key over them, instead of its own `id`.
- Mark personal-data fields with a `-- personal data` comment.
- Use plain types: `text`, `integer`, `numeric`, `boolean`, `date`, `timestamptz`.
- The storage for a retrieval corpus (chunks and embeddings) is set up when retrieval is built. Do not draft it here. Add one comment noting that it is separate. If the plan stores a per-session corpus of the user's own material in a named table, draft that table like any other.

After showing the draft, walk the owner through it in three or four plain sentences: which table is the centre, how the others hang off it, and which access notes matter most.
