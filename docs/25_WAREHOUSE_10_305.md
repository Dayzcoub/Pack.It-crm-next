# 25 Warehouse 10.305

Decision: the `Accept proposal` form includes a separate `Choose another result` action.

Behavior:
- clicking `Choose another result` closes the proposal-acceptance flow;
- the system opens the normal shortage action form;
- the user can then select any available result type and complete a separate final action;
- this action is not treated as proposal acceptance or acceptance with adjustment.

MVP:
- the button is available directly in the proposal-acceptance form;
- leaving the acceptance flow does not modify or delete the original proposal;
- the normal shortage action form opens for warehouse keeper, admin, or director;
- the original proposal remains visible in history;
- the final result is logged as a separate action;
- no proposal-acceptance notification is sent for the separate action.
