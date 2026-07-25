# 25 Shortages 10.346

Decision: the message explaining that a shortage is no longer displayed in the current list remains informational and does not include a `Reset filters` action.

Behavior:
- when the shortage disappears because of the active filters or updated list state, the interface shows the explanatory message under the shortage-list heading;
- the message does not provide a one-click filter reset;
- the user changes or clears filters through the normal list-filter controls;
- the message remains visible according to decision 10.345, until the list is refreshed or the filters change;
- focus remains on the shortage-list heading according to decision 10.344.

Architecture binding:
- the message and absence of an inline reset action are transient `apps/web` presentation behavior;
- the message does not change shortage state, filters, permissions, history, audit records, or notifications;
- filter changes use the normal list-query and projection flow;
- no `shortages` command or domain event is created by showing or dismissing the informational state.

MVP:
- no `Reset filters` button is rendered beside the message;
- the active filters remain unchanged;
- normal filter controls remain available;
- the message clearly explains why the previously active shortage is no longer visible;
- accessibility behavior from decisions 10.343–10.345 remains preserved.
