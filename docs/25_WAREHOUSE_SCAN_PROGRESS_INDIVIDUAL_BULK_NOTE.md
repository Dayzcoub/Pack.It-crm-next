# 25 Warehouse — Individual and Bulk Scan Progress Note

## 10.238. Individual vs bulk item progress

Decision: warehouse scanning uses a mixed model. Not every item needs an individual QR/barcode label.

Item accounting modes:
- individual — item is scanned and tracked one by one;
- bulk — item type/row is scanned or selected, then quantity is confirmed.

Rules:
- expensive, serial, unique, or operationally important items should use individual mode;
- mass items such as cables, adapters, consumables, small hardware, and similar items can use bulk mode;
- individual items count progress by pieces;
- bulk items count progress by row and/or confirmed quantity;
- progress counters should support both modes;
- QR/barcode labels are not required for every single bulk item.

Examples:
- individual: 7 / 10 speakers scanned;
- bulk: cable row requires 20 pcs, user confirms 20 pcs;
- combined progress may show scanned individual items, confirmed rows, and confirmed total quantity.

Purpose:
- avoid unnecessary labeling work;
- keep warehouse scanning practical;
- support both precise asset tracking and fast bulk confirmation.

MVP approach:
- add item/row accounting mode: individual or bulk;
- individual mode uses per-item scan;
- bulk mode uses row scan/selection plus quantity confirmation;
- progress UI accounts for both modes.
