# 25 Shortages 10.328

Decision: if saving a shortage-resolution action fails because of a server or network error, the form remains open, preserves all entered data, and re-enables the Save button for another attempt.

Behavior:
- the in-progress form is not closed or reset after a transport or server failure;
- the selected result, mandatory reason or explanation, general comment, quantities, and other entered values remain unchanged;
- the temporary saving state ends and the Save button becomes available again;
- the form shows a clear non-destructive error message explaining that the action was not confirmed;
- the user may correct data or retry the same submission;
- a failed request does not create a successful shortage resolution, notification, domain-history entry, or success audit event;
- the original shortage and proposal remain unchanged until a request is successfully completed.

Architecture binding:
- preservation of draft form state and restoration of interactive controls are responsibilities of the shortage-resolution interface in `apps/web`;
- `shortages.resolve` remains the only application command that may complete the separate resolution;
- the server must treat the action as completed only after its transaction succeeds;
- notifications are emitted only after the source action has been committed successfully;
- audit records a completed resolution only after success; technical failures may be logged separately without being represented as completed domain actions;
- retry behavior must be safe against accidental duplicate completion if the client did not receive a response to a request that may have reached the server.

MVP:
- network and server errors leave the form open;
- all user-entered values are preserved;
- the Save button becomes active again after the failed attempt;
- an understandable failure message is displayed;
- no successful domain action or notification is created solely because the client attempted to save;
- the user can retry without filling the form again.
