# 25 Shortages 10.329

Decision: when the connection fails after submission and the client cannot determine whether the shortage action was committed, the form must first reconcile against the current shortage state before allowing another submission.

Behavior:
- the form remains open and preserves all entered values while the outcome is unknown;
- the save button stays unavailable while the reconciliation check is in progress;
- the client requests the current shortage state and relevant latest resolution data from the server;
- if the submitted action is already reflected in the current shortage state, the form treats the operation as successful, shows success feedback, and closes;
- if the action is not reflected and the shortage still permits the same operation, the form restores the save button and allows the user to retry;
- if the shortage changed in another way, the form does not resend the stale command and instead shows that the shortage state has changed;
- the client must not infer success only from the absence of an error response.

Architecture binding:
- `shortages` remains the source of truth for the current shortage state and completed resolution actions;
- the reconciliation read is a query/read-model operation and does not create a domain-history or audit event by itself;
- the original write command still requires `shortages.resolve` and server-side authorization;
- the server must support idempotent command handling or an equivalent operation identifier so reconciliation can reliably distinguish an already-applied action from an unrelated state change;
- notifications and audit records are produced only by the successfully committed source action, not by the reconciliation request or repeated client checks;
- transient pending, reconciliation, and retry states belong to the form in `apps/web`.

MVP:
- an unknown submission outcome never immediately enables blind resubmission;
- the current shortage state is checked first;
- an already-applied action is shown as success without creating a duplicate;
- retry is enabled only when the action was not applied and remains valid;
- all unsaved form values are preserved until reconciliation produces a definite result.
