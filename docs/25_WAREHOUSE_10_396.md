# 25 Shortages 10.396

Decision: when an edit lock on a shortage proposal is released, all users currently viewing that proposal receive the updated availability state in real time.

Behavior:
- the stale `currently edited by …` indication is removed without requiring a page refresh;
- the proposal becomes visibly available for editing again as soon as the lock release is confirmed by the server;
- the update applies whether the lock was released normally, automatically after inactivity/disconnect, or administratively;
- users remain in their current read-only view until they explicitly choose to start editing and successfully acquire a new lock;
- no user is granted the released lock automatically.

Architecture binding:
- lock ownership and release remain authoritative on the server;
- real-time propagation is presentation/session synchronization and must not be treated as the source of truth;
- releasing a lock does not create a shortage-domain resolution event by itself;
- administrative forced unlock audit requirements remain governed by decision 10.393.

MVP:
- viewers see lock availability change without refreshing the page;
- the UI immediately removes the previous editor indicator and enables the normal edit-entry action;
- acquiring the next lock remains an explicit server-confirmed action.
