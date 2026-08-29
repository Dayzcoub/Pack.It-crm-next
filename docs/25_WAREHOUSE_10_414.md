# 25 Shortages 10.414

Decision: restoring `shortages.propose_resolution` to a user does not automatically reactivate proposals that were previously auto-closed because that permission was lost.

Behavior:
- proposals closed under decision 10.413 remain closed and stay in shortage history;
- permission restoration does not reopen or revive those proposals;
- if the shortage is still open and a proposal is still needed, the user creates a new proposal;
- the new proposal is a separate domain object/action and does not overwrite or replace the historical closed proposal;
- any current shortage quantity and state rules apply to the newly created proposal.

Architecture binding:
- `shortages` owns proposal lifecycle and preserves the previous closed proposal as history;
- permission restoration changes authorization for future actions only and does not mutate historical proposal state;
- `audit` records the relevant permission and proposal lifecycle actions independently where required.

MVP:
- previously closed proposals remain visibly closed after permission restoration;
- no automatic reopen action is performed;
- the restored user can create a new proposal if they again have `shortages.propose_resolution` and the shortage remains open.
