# 25 Shortages 10.295

Decision: if an assigned user's proposal is accepted only in part, treat it as acceptance with adjustment rather than as an unrelated separate action.

Architecture binding:
- the workflow and remaining quantity are owned by `shortages`;
- the confirmer must have `shortages.accept_proposal` within the applicable scope;
- job titles such as warehouse keeper, admin, or director do not grant this permission automatically.

Example:
- assigned user proposes `found: 3`;
- an authorized confirmer confirms `found: 2`;
- the proposal is recorded as accepted with adjustment;
- only the confirmed quantity affects the shortage balance.

MVP:
- partial acceptance is linked to the original proposal;
- shortage domain history shows both the proposed and confirmed values;
- `shortages` produces the acceptance-with-adjustment event after a successful transaction;
- `notifications` delivers the corresponding notification to the assigned user;
- the remaining shortage stays open if the confirmed quantity does not cover it fully;
- `audit` records the significant action separately.