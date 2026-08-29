# 25 Warehouse 10.435

Decision: physical and accounting stock balances must never be edited directly. Every stock change is produced only by an explicit warehouse operation.

Canonical rule:
- no UI, admin tool, API, migration helper, or privileged role may directly overwrite an inventory balance as an ordinary business action;
- stock changes occur only through a typed warehouse operation such as receipt, issue, return, transfer, writeoff, inventory count adjustment, or another explicitly modeled stock movement;
- every applied operation uses the canonical `WarehouseOperation` envelope from 10.433;
- once applied, the operation is immutable;
- mistakes are corrected by a new compensating or corrective operation rather than rewriting the prior stock history;
- the resulting stock balance is a consequence of committed operations, not an independently editable business value.

Architecture binding:
- `inventory` owns stock balances and validates resulting inventory state;
- `warehouse-operations` owns warehouse execution workflows where applicable;
- operation-specific bounded contexts may initiate stock-changing use cases, but they must do so through explicit committed operations and must not mutate inventory storage directly;
- PostgreSQL remains the source of truth;
- `audit` independently records significant actions and does not replace stock-operation history.

MVP:
- remove the concept of direct balance editing from the business model;
- even administrator corrections must be represented as explicit inventory adjustment operations with actor, timestamp, reason/comment where required, and references;
- current stock is derived from successfully committed warehouse operations and inventory state transitions.
