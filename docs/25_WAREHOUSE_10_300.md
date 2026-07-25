# 25 Shortages 10.300

Decision: if an authorized confirmer keeps the same result type but changes its reason or explanation, treat the action as acceptance of the assigned user's proposal with adjustment.

Architecture binding:
- the workflow owner is `shortages`;
- the confirmer must have `shortages.accept_proposal` within the applicable scope;
- a changed explanation and its adjustment reason are stored in shortage domain history;
- notifications and audit are separate downstream concerns.

Examples:
- assigned user proposes `write_off` with reason `damaged during loading`;
- an authorized confirmer keeps `write_off` but changes the reason to `damaged during operation`;
- the proposal is accepted with adjustment;
- assigned user proposes `accounting_error` with one explanation;
- the authorized confirmer keeps `accounting_error` but replaces the explanation;
- the proposal is accepted with adjustment.

MVP:
- keeping the same result type allows acceptance with adjustment;
- changed reason or explanation is stored as the corrected shortage result data;
- the confirmer must provide a mandatory adjustment reason explaining why the proposal was changed;
- shortage domain history shows the original proposal, corrected reason or explanation, and adjustment reason;
- after successful commit, `shortages` produces an event for `notifications`;
- `write_off` and `accounting_error` consequences are executed through `warehouse-operations` or `inventory` public use cases rather than direct shortage-table side effects.