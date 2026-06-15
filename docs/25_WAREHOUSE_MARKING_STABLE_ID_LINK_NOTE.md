# 25 Warehouse — Stable ID / Card Link Marking Note

## 10.229. What QR/barcode should encode

Decision: QR/barcode should encode a stable internal item ID or a short link/token to the item card. Serial number and inventory number remain fields inside the item card, not the core code value.

Rules:
- code value should be stable and independent from visible item names;
- QR can open item card via internal/app/web link;
- barcode can encode the same stable ID or short token;
- serial number, inventory number, category, status, and history are stored in the item card;
- changing serial number, item name, category, or supplier must not require relabeling the code;
- scanning opens item card or triggers the current workflow action: handout, return, inventory, repair, etc.

Purpose:
- keep labels durable over the item lifecycle;
- avoid relabeling when human-readable fields change;
- make QR and barcode modes use the same internal identity model.

MVP approach:
- generate stable asset_uid per warehouse item;
- encode asset_uid or short item-card link/token in QR/barcode;
- keep serial/inventory numbers as editable item card fields.
