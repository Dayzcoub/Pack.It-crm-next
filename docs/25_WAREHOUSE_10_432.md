# 25 Warehouse 10.432

Decision: all applied warehouse operations use one immutable-action model. A completed warehouse action is never edited retroactively; mistakes are corrected by a new explicit compensating or corrective action that references the original operation and preserves the full history.

Canonical rule:
- every applied warehouse operation is append-only from the domain-history perspective;
- completed actions are immutable business facts;
- corrections do not rewrite the original operation;
- a correction is a new operation with its own actor, timestamp, permissions, reason and domain effects;
- where appropriate, the corrective action references the operation it compensates or corrects;
- current warehouse state is derived from the valid sequence of applied operations, not from silent mutation of historical records;
- the same principle applies across shortage resolution, inventory balance corrections, warehouse write-offs and other warehouse-operation use cases;
- draft or not-yet-applied forms may still be edited according to their own workflow rules; immutability begins once the operation is successfully applied.

Architecture binding:
- `warehouse-operations`, `inventory`, `shortages`, `subrent` and other warehouse-related bounded contexts follow the same applied-action invariant;
- each bounded context remains owner of its own domain transition and validation;
- correction use cases must validate current state and authorization before applying a compensating action;
- PostgreSQL remains the source of truth for current state and persisted operation history;
- `audit` independently records significant actions and corrections;
- no application path may implement a correction by rewriting an already applied domain action in place.

MVP:
- applied warehouse operations are immutable;
- operational mistakes are fixed through explicit corrective/compensating actions;
- original and corrective actions remain visible in history;
- the rule is shared across warehouse domains instead of being redefined separately for each operation type.
