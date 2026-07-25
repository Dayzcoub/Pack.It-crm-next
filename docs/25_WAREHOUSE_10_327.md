# 25 Shortages 10.327

Decision: while a shortage action is being submitted, the `Save` button is disabled and shows an explicit saving state.

Behavior:
- the first valid submit starts the server request;
- the `Save` button becomes disabled immediately after submission starts;
- the button displays a visible loading or `Saving…` state;
- repeated submissions are prevented while the request is in progress;
- other controls that could invalidate the submitted payload may also be temporarily disabled where needed;
- the form remains open until the server confirms success.

MVP:
- only one `shortages.accept_proposal` or `shortages.resolve` command may be in flight from the form at a time;
- disabling the button is a UI safeguard and does not replace server-side idempotency and concurrency checks;
- submitted values remain visible while saving;
- on success, the normal successful-action flow runs;
- on failure, the form remains available for recovery according to the following decisions.
