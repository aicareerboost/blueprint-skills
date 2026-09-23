# Where does the answer live?

Read this before proposing the routing table. The source of an answer decides how the product is built and how it is tested. Choosing the wrong one does not produce an error. It produces a confident answer that happens to be wrong.

## The three patterns

| | A query over our tables | Retrieval over documents | A query the model writes |
|---|---|---|---|
| Also called | Plain SQL | RAG (retrieval-augmented generation) | Text-to-SQL, "chat with my data" |
| Who writes the question | The team, at build time | The user, open-ended | The user, open-ended |
| Shape of the data | Rows and columns | Documents: policies, guides, articles, notes | Rows and columns |
| What the model does | Nothing. It is not in the path. | Reads the passages that come back and writes an answer from them | Writes a query, then reads and phrases the result |
| What can go wrong | Only the query the team wrote | Finding the passage, and the answer written from it | Translating the question into a query |

## How to tell them apart

Ask one question: **does a passage exist somewhere that contains this answer, or does the answer have to be computed?**

- A total, an average, a count, a ranking, or anything over a date range is computed. Retrieval cannot answer it, because no passage contains it. It will try anyway, and the number it gives will look real.
- A rule, a definition, a procedure, or guidance is a passage. Retrieval can find it. A query cannot.
- A computed answer to a fixed question the team knows in advance, such as a dashboard figure, is a query over our tables.
- A computed answer to an open-ended question the user phrases, such as "which team skipped the most meetings last month?", is a query the model writes, unless the model only picks from a fixed list the team wrote (see below).

If you cannot decide, the question is probably two questions. "Is my team taking more leave than the policy allows?" needs a count (a query) and a policy passage (retrieval). Split it into two rows.

## Edge cases: map them to the three, do not add a fourth

- **Content the user supplies at run time.** Pasted notes, uploads, and interview transcripts are **retrieval over documents**. The corpus is the user's own material for that session: small, supplied fresh each time, and often sent to the model whole. The row's reason says so, and the corpus section records who supplies it, whether it is kept after the session, and what sensitivity applies. A judgment the model makes over that input ("which of these complaints matter most?") is one row, not a computed half and a passage half.
- **The model picks from a fixed list.** The user types freely, but the model only maps the question to something the team defined: a known survey variable, a set segment, one of the team's queries. That is **a query over our tables**, with "the model picks which one" in the reason. The words it maps from still need fixed definitions, exactly as for a query the model writes.
- **Fixed text and declined questions are not routes.** Wording written into the product (help text, a "how we checked this" explanation, an error message) is not retrieved, even though a passage exists. A question the product deliberately refuses (for example, "why did they cancel?" when the data cannot show cause) has no source. List both as notes beneath the routing table, with the sentence the product shows. Never create a corpus for fixed text.

## Why the third pattern needs extra care

A bad retrieved answer often reads uncertain. A bad model-written query returns a clean, confident number that answers a slightly different question. Nothing signals the error. The only way to catch it is to compare against a query you trust.

The model also has to know what the owner's words mean in the data. "Completed", "active", "revenue", or "on time" each need a definition that only the product owner can give, for example whether a rescheduled meeting counts as held. Those definitions are a spec for the data and belong in the data plan.

A model that writes queries is also a model that could write changes. The plan must say what it may read and what it must never write, change, or delete.

## When documents disagree

Retrieval can work perfectly and still return two passages that contradict each other, such as an old and a new version of a policy. That is a corpus problem, not a search problem. The owner decides: name one source as authoritative, show both and flag the conflict, or decline to answer until a person resolves it. The plan records which.

## What each pattern means for tests

The routing decision also decides the shape of the test cases written later with `/golden-set`:

- **A query over our tables:** the result matches a query the team trusts.
- **A query over our tables where the model picks which one:** the model picked the right one, and the result matches the trusted query.
- **Retrieval over documents:** the passage was in the corpus, it came back, and it ranked high enough to be used.
- **Retrieval over the user's own material, sent whole:** every claim cites an item the user supplied, and nothing cites an item they did not.
- **A query the model writes:** two checks. The model wrote the right query, and it read the result correctly.
