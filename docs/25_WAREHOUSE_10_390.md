# 25 Shortages 10.390

Decision: only one authorized user may edit and decide on the same shortage proposal at a time.

Behavior:
- opening the proposal for decision acquires an exclusive editing lock;
- other authorized users may still open the proposal in read-only mode;
- the read-only view clearly identifies the active editor using a user-facing display name, for example: `Сейчас редактирует: Иван Петров`;
- other users cannot change values or submit a competing decision while the lock is active;
- the lock owner may save the final decision or close the form without saving;
- when the lock is released, another authorized user may enter editing mode;
- the active-editor indicator contains no internal user identifiers.

Architecture binding:
- the lock protects the `shortages` decision use case from concurrent editing;
- lock acquisition and release are transient application coordination state and do not themselves create a shortage history record, audit event, or notification;
- the final successful shortage action remains the source of domain history, audit, and notification side effects.

MVP:
- one editor per proposal;
- all other users receive a read-only view;
- the interface shows the active editor's user-facing name;
- a second final decision cannot be submitted while the lock is active.
