# 25 Shortages 10.344

Decision: if the shortage that should receive focus is no longer visible in the current list or filter after refresh, focus moves to the shortages list heading and the interface explains that the record is no longer displayed.

Behavior:
- after the recovery mode is closed, the shortage list is refreshed from the current source state;
- the interface first tries to restore focus to the updated shortage card or row according to decision 10.343;
- if the shortage is absent because its state changed, it was removed from the current result set, or it no longer matches the active filter, focus moves to the shortages list heading;
- an accessible status message explains that the shortage is no longer displayed in the current list or filter;
- focus does not jump to an unrelated visible shortage;
- active filters and list position remain unchanged unless another established rule explicitly changes them.

Architecture binding:
- focus placement and the explanatory message are transient `apps/web` presentation behavior;
- visibility is determined from the refreshed shortage read model and the active client-side list/filter state;
- this fallback does not invoke `shortages.resolve`, `shortages.accept_proposal`, or any other shortage command;
- no shortage history, audit event, or notification is created by focus recovery;
- PostgreSQL-backed read projections remain authoritative for whether the shortage is currently present in the result set.

MVP:
- attempt to focus the updated shortage first;
- if it is not rendered in the current list, focus the list heading;
- announce that the record is no longer displayed;
- do not focus the first visible shortage as a substitute;
- do not reset the user's filters automatically.
