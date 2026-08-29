# 25 Warehouse 10.434

Decision: the entire warehouse domain is normalized around conventional WMS/ERP concepts, terminology, lifecycle rules, and audit practices so that an experienced external warehouse/ERP specialist can understand the model without learning PACK.IT-specific mechanics first.

Canonical principle:
- prefer established warehouse concepts and names over custom workflow inventions;
- introduce PACK.IT-specific behavior only where the rental/event-production business genuinely requires it;
- when an older decision conflicts with the canonical WMS model established by 10.430-10.434, the canonical model wins and the older rule is treated as superseded to the extent of the conflict;
- already superseded rules remain superseded, including proposal quantity reservation from 10.424-10.426 and strict proposal FIFO from 10.428-10.429.

Canonical warehouse concepts:
- `InventoryBalance` / stock balance is current state derived from committed warehouse-domain actions, not a manually rewritten business history;
- `WarehouseTask` represents planned or executable warehouse work;
- `WarehouseOperation` represents an applied/committed warehouse fact and uses the common envelope from 10.433;
- `Reservation` / `Allocation` represents an explicit stock commitment and is separate from proposals, comments, drafts, and exception-resolution suggestions;
- `PhysicalInventory` represents physical counting/recounting and reconciliation of system stock with actual stock;
- `InventoryAdjustment` represents a posted correction/difference with an explicit reason and traceable source;
- `WorkException` / `ShortageCase` represents an exceptional warehouse situation that requires resolution without itself mutating stock merely by existing;
- `ResolutionAction` is the canonical applied action that resolves all or part of a shortage/exception and records whether it originated directly or from a proposal;
- `Audit` remains an independent security/compliance trail and does not replace warehouse operation history.

Lifecycle rules:
- drafts, proposals, forms, recommendations, and other intentions are workflow entities, not applied warehouse operations;
- intentions do not change stock or shortage remainder until an authorized action is actually committed;
- applied warehouse operations are immutable business facts;
- errors are corrected by new compensating/corrective operations linked to the original operation, never by silently rewriting the prior fact;
- current quantities and statuses are recalculated from successfully committed domain actions;
- concurrency is validated against the latest state at commit time;
- exceptional situations use a common exception workflow instead of separate bespoke state machines for each screen;
- standard domain state transitions are preferred over UI-specific behavior rules.

Terminology and onboarding:
- architecture and code should use stable conventional English domain names where practical;
- the Russian UI may use clear localized business labels without changing the underlying domain meaning;
- documentation must define any PACK.IT-specific term by mapping it to the nearest conventional WMS/ERP concept;
- an external specialist should be able to identify receipt, issue, movement, reservation/allocation, count, adjustment, exception, task, and posted operation without needing project-specific interpretation.

Architecture binding:
- bounded contexts keep ownership of their domain invariants; normalization does not create a single god-object warehouse module;
- `inventory` owns stock state and accounting corrections;
- `reservations` owns explicit stock commitments;
- `shortages` owns shortage/exception state and resolution workflow;
- `warehouse-operations` owns operational warehouse execution where already defined by the architecture;
- `subrent` remains a separate business capability and integrates through explicit domain actions rather than masquerading as on-hand warehouse stock;
- PostgreSQL remains the source of truth;
- all cross-context effects occur through named application use cases and explicit transaction/integration boundaries.

MVP:
- use conventional WMS semantics as the default design rule for every warehouse-related feature;
- do not invent special reservation, priority, correction, or exception mechanics unless a concrete PACK.IT business requirement cannot be represented by the canonical model;
- keep committed operations traceable and immutable;
- keep workflow intentions separate from committed stock-changing facts;
- document deviations from standard WMS behavior explicitly and justify why they exist.
