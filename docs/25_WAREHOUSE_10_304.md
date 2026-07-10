# 25 Warehouse 10.304

Decision: the result type cannot be changed inside the `Accept proposal` form.

Behavior:
- the form keeps the result type from the assigned user's proposal;
- the result type is read-only in the acceptance form;
- allowed adjustments may be made only within that same result type;
- to use a different result type, the confirmer must close the acceptance form and perform a normal separate action.

MVP:
- the proposal result type is clearly shown but cannot be edited;
- no result-type selector is available in the acceptance form;
- switching to another result type never creates proposal acceptance or acceptance with adjustment;
- the original proposal remains visible in history;
- a different final result is logged as a separate action by warehouse keeper, admin, or director;
- no proposal-acceptance notification is sent when a separate action with another result type is used.
