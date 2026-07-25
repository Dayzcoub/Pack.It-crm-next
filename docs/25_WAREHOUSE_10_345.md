# 25 Shortages 10.345

Decision: when the shortage no longer appears in the current list or filter after the recovery mode is closed, the explanatory message is shown under the shortages list heading and remains visible until the list is refreshed or the filters are changed.

Behavior:
- focus moves to the shortages list heading according to decision 10.344;
- an explanatory message appears directly under the heading;
- the message states that the previously active shortage is no longer displayed in the current list or filter;
- the message remains visible while the current list state is unchanged;
- refreshing the list or changing any filter clears the message;
- the message is not a temporary toast and does not disappear automatically;
- the user may continue navigating and working with the visible shortages while the message is present.

Accessibility:
- the message is programmatically associated with the list heading or list region;
- moving focus to the heading makes the contextual message available to assistive technologies;
- the message does not unexpectedly steal focus after it has been shown;
- removal of the message after refresh or filter change does not trigger an additional focus move.

Architecture binding:
- the explanatory message and its lifetime are transient `apps/web` presentation state;
- showing or clearing the message does not mutate shortage state, list filters, or server data;
- no `shortages` command, domain event, audit record, or notification is created by this UI behavior;
- the actual list contents remain based on the current server-backed read projection and active filters.

MVP:
- show the message under the shortages list heading;
- keep it visible until list refresh or filter change;
- do not auto-dismiss it by timer;
- keep the updated list fully usable while the message is visible.
