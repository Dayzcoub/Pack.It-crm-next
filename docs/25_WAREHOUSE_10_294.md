# 25 Shortages 10.294

Decision: if the final result differs from the assigned user's proposal, do not send a separate notification to the assigned user.

Architecture binding:
- the workflow owner is `shortages`;
- `shortages` records the proposal and final decision in shortage domain history;
- `notifications` only delivers notifications produced from successful shortage events;
- `audit` records the significant action separately and does not replace shortage history.

MVP:
- notify the assigned user only when their proposal is accepted or accepted with adjustment;
- no separate notification is produced for a different final decision;
- the proposal and final decision remain visible in shortage domain history;
- the separate final action requires `shortages.resolve` and is logged normally;
- no role name bypasses application authorization.