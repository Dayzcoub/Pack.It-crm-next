# 25 Shortages 10.296

Decision: when an authorized confirmer accepts an assigned user's proposal with an adjustment, they must provide a reason for the change.

Architecture binding:
- the workflow owner is `shortages`;
- the confirmer must have `shortages.accept_proposal` in the applicable scope;
- the adjustment reason is part of shortage domain history;
- `audit` stores a separate significant-action record.

Example:
- assigned user proposes `found: 3`;
- an authorized confirmer confirms `found: 2`;
- the action is treated as acceptance with adjustment;
- the confirmer explains why the confirmed value differs from the proposal.

MVP:
- the adjustment reason is required before the use case can commit;
- the reason is stored together with the confirmed shortage result;
- shortage domain history shows the original proposal, confirmed result, and adjustment reason;
- after successful commit, `shortages` produces an event for `notifications`;
- the remaining shortage stays open if the confirmed quantity does not cover it fully;
- no role name bypasses the permission check.