# 25 Warehouse 10.439

Decision: changing an equipment unit from `Blocked` back to `Ready` requires a short explicit reason/comment.

Behavior:
- `Blocked -> Ready` is an applied warehouse/inventory operation and is recorded through the canonical `WarehouseOperation` envelope;
- the user must provide a short reason such as `проверено`, `отремонтировано`, or `неисправность не подтвердилась`;
- the prior blocking reason remains preserved in history and is never overwritten;
- restoring `Ready` makes the unit eligible for availability calculations again, subject to reservation and other inventory rules;
- the operation records actor, timestamp, affected unit, and the unblocking reason;
- the operation is immutable after commit; later mistakes are corrected with a new compensating/corrective operation under the common warehouse rules.

Architecture binding:
- `inventory` owns the equipment availability state and validates the `Blocked -> Ready` transition;
- the change must be performed through a named application use case rather than direct record editing;
- `WarehouseOperation` supplies the common operational envelope and traceability;
- `audit` may independently record the significant action but does not replace inventory history.

MVP:
- every `Blocked -> Ready` transition requires a short comment;
- the comment is stored with the applied operation;
- the unit becomes available only after the transition succeeds.
