# 25 Shortages 10.391

Decision: an exclusive proposal-editing lock is released automatically when the editing user is confirmed disconnected or remains inactive for a short period.

Behavior:
- normal explicit exit from the decision form releases the lock immediately;
- confirmed loss of the editing session releases the lock automatically;
- if disconnection cannot be confirmed, the lock expires after a short inactivity timeout;
- any valid activity from the lock owner refreshes the lock lifetime;
- after release, another authorized user may acquire the editing lock;
- users viewing the proposal must see the lock state update without needing to recreate the shortage action;
- automatic lock release does not itself accept, reject, withdraw, or otherwise change the proposal.

Architecture binding:
- the exclusive lock is transient coordination state and is not the business status of the shortage or proposal;
- `shortages` remains the owner of proposal and shortage state;
- automatic lock release creates no shortage resolution, notification, or inventory side effect;
- unsaved form values are not persisted as a domain result merely because the lock expires.

MVP:
- release the lock on explicit form exit;
- release it on confirmed disconnect;
- otherwise release it after a short inactivity timeout;
- refresh the timeout while the owner remains active;
- make the proposal available for editing by another authorized user after release.
