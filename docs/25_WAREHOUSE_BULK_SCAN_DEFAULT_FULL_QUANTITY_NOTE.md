# 25 Warehouse — Bulk Scan Default Full Quantity Note

## 10.240. Bulk scan quantity behavior

Decision: for bulk items, scanning the row/item type confirms the full required quantity by default. User can manually adjust the quantity if needed.

Rules:
- bulk item scan does not require scanning every piece;
- scan sets confirmed quantity to the required quantity by default;
- user can edit confirmed quantity manually;
- edited quantity is used in progress and final confirmation;
- if quantity is edited below required quantity, document remains partially confirmed for that row.

Purpose:
- make bulk scanning fast;
- avoid unnecessary per-piece scanning for cables, adapters, consumables, small hardware, and similar items;
- still allow correction when actual quantity differs.

MVP approach:
- scan or select bulk row;
- prefill confirmed quantity with required quantity;
- allow manual quantity correction before final confirmation.
