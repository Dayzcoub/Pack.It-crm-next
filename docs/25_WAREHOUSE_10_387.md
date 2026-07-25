# 25 Shortages 10.387

Decision: after withdrawing a proposal, the responsible person may submit a new proposal for the same open shortage.

Behavior:
- the withdrawn proposal remains in shortage history with its withdrawn status;
- a new proposal is created as a separate record and does not restore or overwrite the withdrawn proposal;
- only the new proposal is considered active for subsequent acceptance, adjustment, withdrawal, or final resolution;
- the shortage remains open until an authorized user records a final result;
- normal proposal notification rules apply to the newly submitted proposal.

Architecture binding:
- `shortages` owns proposal lifecycle, active status, withdrawal, and proposal history;
- submitting the new proposal requires `shortages.propose_resolution`;
- the new proposal is recorded only after the source command succeeds;
- `notifications` delivers the standard new-proposal notification after successful creation;
- `audit` records both the earlier withdrawal and the new proposal as separate significant actions.

MVP:
- a withdrawn proposal does not block a later proposal from the same responsible person;
- the new proposal has its own identity, timestamp, author, and content;
- withdrawn proposals remain read-only in history and cannot become active again.
