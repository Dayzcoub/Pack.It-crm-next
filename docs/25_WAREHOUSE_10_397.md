# 25 Shortages 10.397

Decision: the exclusive editing lock applies only to the specific proposal being reviewed, not to the entire shortage.

Behavior:
- while one user edits a proposal, that proposal is read-only for other users;
- other proposals attached to the same shortage remain independently available according to their own state and permissions;
- other shortage actions are not blocked merely because one proposal is being edited;
- any final shortage-level command must still validate the current shortage state at save time and reject stale or conflicting actions rather than silently overwrite newer state.

Architecture binding:
- proposal lock state is transient coordination state for the proposal editing flow;
- the `shortages` bounded context remains authoritative for shortage state and final command validation;
- a proposal lock does not itself create shortage history, audit events, or notifications unless another documented rule explicitly requires them.

MVP:
- locking is scoped to one proposal;
- parallel work on other proposals/actions for the same shortage remains possible;
- save-time validation prevents incompatible concurrent results from being committed.
