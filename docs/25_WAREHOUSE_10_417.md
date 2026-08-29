# 25 Shortages 10.417

Decision: when a warehouse user is actively reviewing a proposal that is automatically closed because its author lost `shortages.propose_resolution`, no separate notification is sent to that warehouse user.

Behavior:
- the proposal is closed immediately according to decision 10.416;
- the active review lock is released;
- the already-open review form becomes read-only;
- the form clearly shows that the proposal is no longer valid and states the reason for closure;
- no additional push, inbox, or separate notification is required for the reviewing warehouse user;
- the author notification defined by decision 10.415 remains unchanged.

Architecture binding:
- `shortages` owns the immediate proposal closure, lock release, and resulting proposal state;
- the review UI reflects the authoritative shortage/proposal state in real time or on reconciliation;
- `notifications` does not emit a warehouse-user notification for this case;
- `audit` records the significant permission-driven closure independently where required by the audit policy.

MVP:
- the warehouse review form switches to read-only as soon as the closure is observed;
- the closure reason is visible in the form itself;
- no separate warehouse notification is generated.
