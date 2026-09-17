# Controls and timing

No single control carries a system. Combine several so their gaps rarely line up.

## Six controls

| Control | Type | What it does | Example |
|---|---|---|---|
| Least privilege | Mitigation | Limits what the system can touch | An email assistant can create drafts but cannot send or delete |
| Isolation and allowlists | Mitigation | Keeps untrusted content away from anything with authority | The agent may read only an approved list of websites; test and live data are separate |
| Approval boundaries | Mitigation | Puts a person in front of consequential actions | A human approves every message before it is sent |
| Adversarial evaluations | Mitigation | Finds weaknesses before launch | Testers try to trick the system into leaking data or ignoring a stop instruction |
| Monitoring | Detection | Shows that something is going wrong | An alert fires if the number of records in a table suddenly drops |
| Rollback and kill switch | Contingency | Stops the damage and undoes it | A one-step way to pull a published answer or halt a runaway process |

## Before, during, and after

- **Before the action:** make failure less likely. Least privilege, isolation and allowlists, adversarial evaluations. Most of this is decided in the product design.
- **During the action:** catch it in the act. Approval boundaries and monitoring.
- **After the action:** limit and reverse the damage. Rollback, kill switch, and an update to the risk register so the next version has one fewer gap.

A priority risk should have at least one control in each of the three columns, or a stated reason why not.

## The complete path for a priority risk

Risk scenario → mitigation → contingency → evaluation or detection → guardrail or approval boundary → owner → review trigger.
