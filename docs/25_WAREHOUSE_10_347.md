# 25 Shortages 10.347

Decision: when a shortage disappears from the current list or active filter after a conflict refresh, the informational message identifies the specific shortage that is no longer displayed.

Behavior:
- the message appears under the shortages list heading according to decision 10.345;
- the message includes the user-facing name or position label of the disappeared shortage;
- the identifier must be sufficient for the user to understand which action produced the conflict;
- the message remains informational and does not include a `Reset filters` action according to decision 10.346;
- the message remains visible until the list is refreshed again or the active filters change;
- focus remains on the shortages list heading according to decision 10.344.

Architecture binding:
- the displayed shortage name is read from the latest `shortages` read model returned after the conflict check;
- this message and its lifetime are transient `apps/web` presentation state;
- displaying the name does not recreate, mutate, or retain the disappeared shortage in domain state;
- the conflict refresh remains authoritative and must not be replaced by stale form data;
- no domain event, audit event, notification, or shortage history entry is created by showing or dismissing the message.

MVP:
- the user can identify which shortage disappeared from the current view;
- the message uses the same human-readable name or position label used elsewhere in the shortages interface;
- the message does not expose internal IDs as its primary wording;
- changing filters or refreshing the list removes or replaces the message;
- the current list continues to reflect only the latest server state.
