# 25 Warehouse 10.436

Decision: for MVP, equipment availability uses a deliberately simple two-state inventory condition model: `Ready` or `Blocked`. The reason for blocking is stored separately and does not create additional stock quantity classes.

Canonical quantities and condition semantics:
- `on_hand` = all equipment physically accounted for at the warehouse/location, regardless of whether it is currently usable;
- `reserved` = the part of usable stock committed by confirmed reservations;
- `available` = usable `Ready` stock that is not already reserved;
- `Blocked` equipment remains part of `on_hand` but is excluded from `available` and cannot be issued or newly reserved;
- `shortage` is not an inventory balance bucket; it remains a separate exception/case derived from uncovered demand;
- `subrent` is not automatically part of `on_hand` until equipment is actually received into the warehouse/accounting boundary, if such receipt is modeled.

Equipment condition:
- `Ready` — equipment may participate in availability and normal warehouse operations;
- `Blocked` — equipment is physically present/accounted for but cannot participate in outbound availability;
- reasons such as damaged, needs inspection, under repair, suspected electrical damage, or other operational concerns are stored as block reasons/comments rather than separate inventory states in MVP.

Operational behavior:
- when equipment returns from an event with a problem, the warehouse user may block it as part of the return/inspection workflow;
- blocking does not reduce `on_hand` and does not perform a writeoff;
- restoring a repaired or cleared item to service changes condition back to `Ready` through an explicit warehouse/inventory operation;
- if the item is later deemed irrecoverable, a separate writeoff operation reduces `on_hand`;
- the block operation should retain context such as project/source event and a concise problem comment where available;
- responsibility, repair cost, compensation, service workflow, and detailed incident investigation are not required for MVP and may be introduced later as a separate maintenance/incident capability.

Architecture binding:
- `inventory` owns equipment condition and the resulting availability calculation;
- applied condition changes follow the common immutable `WarehouseOperation` rules established in 10.432–10.435;
- condition changes are not direct balance edits;
- `warehouse-operations` / `inventory` application use cases perform the appropriate named state transition and preserve operation history;
- `audit` remains independent from the domain operation history.

MVP:
- support only `Ready` and `Blocked` as availability-relevant equipment conditions;
- keep block reason separately;
- include `Blocked` in `on_hand` but exclude it from `available`;
- do not introduce separate `Damaged`, `Inspection`, `Repair`, or similar stock buckets unless later operational evidence justifies them.
