# 25 Warehouse — QR and Barcode Mode Note

## 10.227. Warehouse item marking mode

Decision: MVP supports both QR codes and barcodes for warehouse item marking, with a switchable mode.

Rules:
- system should support QR code marking;
- system should support barcode marking;
- company/admin settings can choose the preferred marking mode;
- the marking/scanning workflow should work with both modes where possible;
- switching mode must not break existing item identity.

Purpose:
- support different warehouse habits and label printers;
- keep the system flexible for small and larger companies;
- avoid locking the product into one marking format too early.

MVP approach:
- support both QR and barcode formats;
- add a mode setting for preferred label/scanning format;
- keep the internal item identifier independent from visual code format.
