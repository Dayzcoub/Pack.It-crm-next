# 25 Warehouse 10.441

Decision: project reservations are quantity-based and never bind to equipment serial numbers. Serial-number identity remains an inventory/warehouse concern only.

Canonical model:
- `Reservation` references the catalog/inventory position and reserved quantity;
- a reservation does not store, own, or depend on serial numbers;
- serialized units are tracked separately by `inventory` as physical units belonging to the position;
- serial numbers participate only in physical warehouse operations and inventory condition/discrepancy tracking;
- unit-level markers such as `Ready`, `Blocked`, malfunction, or missing/discrepancy belong to the serialized inventory unit, not to the reservation;
- for quantity-tracked stock the equivalent restrictions are represented as quantities such as `blocked_qty` rather than synthetic serial units.

Availability behavior:
- reservation demand remains stable when one physical serialized unit becomes `Blocked` or otherwise unavailable;
- `Blocked` or missing units reduce the usable `Ready` pool but do not rewrite existing reservations;
- if enough other `Ready` quantity exists, the reservation remains fully covered without any special action;
- if usable `Ready` quantity becomes insufficient to cover confirmed reserved demand, the shortage is derived from the uncovered quantity and handled through the canonical `ShortageCase` exception workflow;
- shortage is quantity-based and does not own serial-number identity.

Warehouse behavior:
- serial numbers may be referenced when executing physical operations such as issue, return, movement, inspection, blocking, unblocking, or recording a missing unit;
- this physical traceability must not leak back into the reservation aggregate;
- replacing one usable serial unit with another unit of the same inventory position does not require changing the project reservation.

Architecture binding:
- `reservations` owns project demand reservation by position and quantity;
- `inventory` owns serialized-unit identity, physical condition, and usable-stock calculation;
- `warehouse-operations` records physical movements and may carry serial-number references where applicable;
- `shortages` owns only the uncovered quantity and its exception-resolution lifecycle;
- no bounded context may introduce a hidden serial-number dependency into `Reservation`.

MVP:
- reservations are always position + quantity;
- serial numbers are never reserved for a project;
- serialized units remain separate inventory records used only for warehouse traceability and condition/discrepancy marks;
- blocked or missing units affect availability through the usable pool, not by editing reservations.
