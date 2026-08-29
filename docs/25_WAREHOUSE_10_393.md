# 25 Shortages 10.393

Decision: an administrator may forcibly release another user's active edit lock, but only through an explicit administrative action with confirmation, a mandatory reason, and an audit record.

Behavior:
- the administrator must explicitly confirm the forced unlock;
- a reason is mandatory before the action can be submitted;
- after successful forced unlock, the previous editor immediately loses edit authority for that proposal;
- if the previous editor still has the form open, it follows the lock-loss behavior from decision 10.392 and becomes read-only while preserving the entered values on screen;
- the proposal itself is not modified merely by releasing the lock.

Architecture binding:
- lock ownership and forced release are concurrency/presentation coordination around shortage proposal editing;
- the administrative forced-unlock action must be recorded by the `audit` bounded context with actor, target lock/proposal reference, reason, timestamp, and outcome;
- forcing a lock release does not by itself create a shortage resolution, notification, inventory mutation, reservation mutation, or warehouse operation.

MVP:
- administrator can force-release an active proposal edit lock;
- confirmation is required;
- reason is required;
- the action is auditable;
- the displaced editor becomes read-only immediately when the client learns the lock was lost.
