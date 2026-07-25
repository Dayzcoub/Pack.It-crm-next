# 25 Shortages 10.304

Decision: the result type cannot be changed inside the `Accept proposal` form.

Architecture binding:
- the acceptance form executes a `shortages` use case;
- opening and submitting it requires `shortages.accept_proposal` within the applicable scope;
- a different result type requires a separate `shortages.resolve` action;
- any resulting `inventory`, `subrent`, or `warehouse-operations` change uses that module's public boundary and permission checks.

Behavior:
- the form keeps the result type from the assigned user's proposal;
- the result type is read-only in the acceptance form;
- allowed adjustments may be made only within that same result type;
- to use a different result type, the confirmer must close the acceptance flow and perform a normal separate action.

MVP:
- the proposal result type is clearly shown but cannot be edited;
- no result-type selector is available in the acceptance form;
- switching to another result type never creates proposal acceptance or acceptance with adjustment;
- the original proposal remains visible in shortage domain history;
- a different final result is logged as a separate shortage action;
- no proposal-acceptance notification is produced for that separate action;
- no job title or system role bypasses application authorization.