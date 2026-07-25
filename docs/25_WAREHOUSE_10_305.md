# 25 Shortages 10.305

Decision: the `Accept proposal` form includes a separate `Choose another result` action.

Architecture binding:
- proposal acceptance belongs to `shortages.accept_proposal`;
- choosing another result leaves the acceptance use case and opens a separate action governed by `shortages.resolve`;
- the separate result coordinates required `inventory`, `subrent`, or `warehouse-operations` use cases through public boundaries;
- `notifications` and `audit` remain downstream concerns and do not own the result.

Behavior:
- clicking `Choose another result` closes the proposal-acceptance flow;
- the system opens the normal shortage action form;
- the user can select any result type allowed by their permissions and scope;
- this action is not treated as proposal acceptance or acceptance with adjustment.

MVP:
- the button is available directly in the proposal-acceptance form;
- leaving the acceptance flow does not modify or delete the original proposal;
- the normal shortage action form opens only for a user authorized by `shortages.resolve`;
- result-specific downstream permissions are also checked before commit;
- the original proposal remains visible in shortage domain history;
- the final result is logged as a separate shortage action;
- no proposal-acceptance notification is produced for the separate action.