# 25 Warehouse 10.440

Decision: apply `Blocked` according to the inventory accounting model instead of forcing all inventory into per-unit tracking.

Behavior:
- for serialized / individually tracked equipment, `Blocked` is applied to the specific inventory unit;
- for quantity-tracked inventory, blocked stock is represented as `blocked_qty` within the relevant stock/location scope;
- `blocked_qty` remains part of physical `on_hand` but is excluded from `available`;
- blocking must never fabricate synthetic serial units solely to represent unusable quantity;
- unblocking returns the same unit or quantity back to `Ready`/available stock through an explicit warehouse operation;
- reasons/comments remain mandatory under decisions 10.438 and 10.439.

Canonical quantity relation:
- serialized stock: availability is derived from units whose inventory state is `Ready`, minus confirmed reservations as applicable;
- quantity stock: `ready_qty = on_hand - blocked_qty`; `available` is derived from `ready_qty` after confirmed reservations/allocation;
- `Blocked` is an inventory state/quantity classification, not a separate shortage and not a write-off.

Architecture binding:
- `inventory` owns stock state and `blocked_qty`;
- `warehouse-operations` records the applied block/unblock operation using the common `WarehouseOperation` envelope;
- applied operations remain immutable and corrections are new linked operations under 10.432–10.433;
- physical quantity changes still require a proper stock operation under 10.435.

MVP:
- support blocking individual serialized assets;
- support `blocked_qty` for bulk/quantity-tracked SKUs;
- keep both models under the same user-facing concepts `Ready` and `Blocked`;
- do not require serialisation of cables, adapters, consumable-like bulk items, or other quantity-tracked stock merely to support blocking.
