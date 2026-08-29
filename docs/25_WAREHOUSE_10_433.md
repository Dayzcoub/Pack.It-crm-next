# 25 Warehouse 10.433

Decision: all applied warehouse operations use a common `WarehouseOperation` envelope while each bounded context keeps ownership of its own domain rules and state transitions.

Canonical envelope:
- operation type;
- actor / author snapshot;
- execution timestamp;
- reason and/or comment where required by the operation;
- references to affected domain entities;
- optional reference to a prior operation being corrected or compensated;
- source/context metadata needed to trace where the operation originated.

Behavior:
- the envelope is a common contract for warehouse-domain operations, not a shared aggregate that replaces bounded-context ownership;
- `inventory`, `reservations`, `shortages`, `subrent`, and `warehouse-operations` continue to own their specific invariants and side effects;
- once an operation is applied, its recorded facts are immutable;
- mistakes are corrected by a new corrective/compensating operation that links back to the operation being corrected;
- the operation chain must preserve the complete business history rather than rewriting prior records;
- user-facing history may present domain-specific labels, but all applied operations remain traceable through the same canonical envelope;
- `audit` independently records significant actions and does not replace the warehouse operation history.

Architecture binding:
- PostgreSQL remains the source of truth;
- application use cases create domain-specific operations inside their owning transaction boundaries;
- the canonical envelope provides consistent identity, authorship, timing, references, and correction linkage across warehouse-related bounded contexts;
- shared envelope fields do not grant one bounded context permission to mutate another bounded context's state directly.

MVP:
- use the common `WarehouseOperation` envelope for all applied warehouse operations;
- keep domain payload and validation owned by the relevant bounded context;
- never edit an applied operation in place;
- represent corrections as new linked operations with full history preserved.
