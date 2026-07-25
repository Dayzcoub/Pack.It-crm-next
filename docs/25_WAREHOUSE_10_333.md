# 25 Shortages 10.333

Decision: closing the read-only recovery view that contains unsaved form data requires explicit confirmation because the data will be permanently removed from the current page session.

Behavior:
- the close action opens a confirmation dialog before the recovery view is dismissed;
- the dialog clearly states that the preserved form data will be deleted and cannot be restored;
- confirming closes the read-only view and removes the preserved data from the current page session;
- cancelling keeps the read-only view open with all preserved data unchanged;
- the confirmation is required only while preserved recovery data still exists;
- after confirmed deletion, reopening the same recovery data is not possible.

Architecture binding:
- the preserved data, confirmation state, and deletion are transient UI state owned by `apps/web`;
- the recovery copy is not persisted to `shortages`, `audit`, or any other backend context;
- confirming or cancelling the dialog does not create domain-history or audit events;
- the actual shortage state remains the current server state shown after the conflict;
- any subsequent shortage action is created through the normal flow and requires the corresponding `shortages` permission.

MVP:
- closing the read-only recovery view cannot silently discard preserved data;
- confirm permanently clears the preserved data for the current page session;
- cancel preserves the view and its contents;
- no backend record is created for the temporary recovery data or its deletion.
