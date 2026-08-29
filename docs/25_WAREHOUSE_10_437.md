# 25 Warehouse 10.437

Decision: an ordinary equipment return defaults the returned unit to `Ready`; the unit is moved to `Blocked` only when a problem is actually detected during return.

Behavior:
- successful standard return restores the unit to normal warehouse availability rules;
- the return workflow does not create an automatic inspection quarantine for every unit;
- if damage, malfunction, uncertainty, or another issue is noticed, the operator explicitly marks that unit `Blocked` and records the blocking reason/comment;
- `Blocked` units remain part of `on_hand` but are excluded from `available` under 10.436;
- a later unblock, write-off, or other state-changing outcome is recorded as a separate warehouse operation rather than by editing the original return in place;
- the return and any resulting state change remain traceable through the canonical `WarehouseOperation` history.

Architecture binding:
- `warehouse-operations` owns the physical return operation;
- `inventory` owns the resulting equipment state and availability projection;
- any transition to `Blocked` must be explicit and auditable;
- applied operations remain immutable and corrections are represented by new linked operations under 10.432–10.435.

MVP:
- normal return -> `Ready`;
- detected problem -> explicit `Blocked` with reason/comment;
- no mandatory inspection/quarantine step for every returned unit.
