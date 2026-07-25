# 25 Shortages 10.392

Decision: if an exclusive proposal-editing lock is automatically released because the active user disconnected or exceeded the inactivity threshold, that user's still-open form immediately switches to read-only mode.

Behavior:
- all values already entered into the form remain visible;
- the form does not silently discard or overwrite the user's local input;
- save and other mutating actions become unavailable while the user no longer owns the lock;
- the interface clearly explains that the editing lock was released because of inactivity or connection loss;
- to continue editing, the user must explicitly request the lock again;
- reacquiring the lock is allowed only if no other eligible user has obtained it in the meantime;
- if another user currently owns the lock, the form remains read-only and identifies that user according to decision 10.390.

Concurrency binding:
- lock ownership is authoritative on the server and must be revalidated before every mutating proposal decision command;
- local form state does not grant permission to save after lock ownership has been lost;
- no shortage state transition, proposal decision, notification, or audit event is created merely by automatic lock release or by switching the form to read-only mode.

MVP:
- an expired lock immediately disables editing and saving;
- entered values remain visible in the current page session;
- the user can explicitly attempt to reacquire the lock and continue from the preserved values if the lock is still available.
