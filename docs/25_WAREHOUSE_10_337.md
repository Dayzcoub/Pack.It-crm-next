# 25 Shortages 10.337

Decision: after a conflict, the recovery mode opens even when all recoverable text fields from the original action are empty.

Behavior:
- the conflicting form closes and the current shortage state is shown;
- the recovery mode opens according to the same conflict flow used for non-empty text data;
- no synthetic text, placeholders presented as recovered values, or copied non-text values are added;
- the mode clearly represents that there are no text values available for manual recovery;
- the user closes the recovery mode separately before starting a new shortage action;
- opening the empty recovery mode does not create or repeat any shortage action.

Architecture binding:
- the empty recovery mode is transient `apps/web` presentation state;
- its contents are not persisted to PostgreSQL and are not part of shortage history;
- opening or closing it does not invoke `shortages.resolve`, `shortages.accept_proposal`, or another source-domain use case;
- it does not create domain events, audit events, notifications, inventory changes, reservations, or warehouse-operation side effects;
- the current shortage read model remains the authoritative state shown after the conflict.

MVP:
- the conflict flow opens recovery mode regardless of whether recoverable text exists;
- empty text values remain empty;
- non-text fields are not displayed as recoverable data;
- no automatic new action is created;
- the mode exists only in the current page session according to decision 10.332.
