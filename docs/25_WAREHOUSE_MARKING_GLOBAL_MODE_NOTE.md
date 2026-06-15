# 25 Warehouse — Global Marking Mode Note

## 10.228. Global QR/barcode marking mode

Decision: QR/barcode mode is a global company-level setting.

Rules:
- company uses one active marking mode at a time;
- if QR mode is selected, all generated labels use QR;
- if barcode mode is selected, all generated labels use barcode;
- do not mix QR and barcode by category or equipment group in MVP;
- switching mode must not change the internal item identity.

Purpose:
- avoid confusion in warehouse scanning;
- keep labels and scanner behavior predictable;
- simplify training and warehouse operations.

MVP approach:
- add one global company setting for marking mode;
- support QR and barcode as options;
- do not add per-category marking mode overrides.
