# 25 Warehouse 10.442

Decision: ordinary warehouse issue and return operations remain quantity-based even for inventory positions that have serial-numbered units; serial numbers are not mandatory in the normal issue/return flow.

Behavior:
- reservations remain expressed only as inventory position + quantity;
- ordinary issue and return operations are also recorded by inventory position + quantity;
- serial numbers are stored separately in `inventory` as identifiers of physical units, but are not required to complete routine reservation, issue, or return workflows;
- serial numbers are used only when a specific physical unit must be identified for an exception or point investigation, including equipment marked `Blocked`, a reported malfunction, a missing unit, or another explicitly serial-specific case;
- a normal quantity-based return does not require the operator to scan or select every returned serial number;
- a normal quantity-based issue does not bind the project reservation to specific serial numbers;
- where a specific serial unit is reported as defective or missing, that serial record may carry the corresponding exception marker/history without changing the quantity-based reservation model.

Architecture binding:
- `reservations` owns project demand reservation by position and quantity and has no serial-number dependency;
- `warehouse-operations` records routine issue/return quantities without requiring serial allocation;
- `inventory` owns serial-number records and per-unit `Ready`/`Blocked` exception state where applicable;
- serial-specific exception handling must not silently rewrite reservation semantics;
- quantity balances remain the source for ordinary availability and shortage calculations, while serial data provides additional physical-unit traceability only where explicitly needed.

MVP:
- no mandatory serial scanning for routine issue or return;
- no serial binding in reservations;
- serial numbers are used for defects, missing equipment, `Blocked` state, and other explicit unit-level exceptions only.
