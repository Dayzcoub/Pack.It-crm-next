# 25 Shortages 10.338

Decision: closing an empty recovery mode requires the same explicit confirmation as closing a recovery mode that contains text.

Behavior:
- the confirmation dialog is shown whenever the user attempts to close recovery mode;
- the rule does not depend on whether recoverable text fields are empty;
- the dialog clearly states that the temporary recovery snapshot will be deleted;
- canceling the confirmation keeps recovery mode open;
- confirming closes recovery mode and permanently removes the temporary snapshot from the current page session;
- after deletion, the snapshot cannot be restored.

Architecture binding:
- recovery mode and its temporary snapshot are transient `apps/web` state;
- opening, canceling, or confirming the close dialog does not invoke a `shortages` use case;
- deleting the temporary snapshot does not change shortage state, domain history, audit records, or notifications;
- no recovery snapshot is persisted to PostgreSQL or restored after the page session ends.

MVP:
- all recovery modes use one close-confirmation flow;
- empty recovery mode is not a special case;
- confirmation is required before deleting the temporary snapshot;
- cancel preserves the mode and snapshot;
- confirm closes the mode and deletes the snapshot for the current page session.
