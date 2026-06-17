# 25 Warehouse — Bulk Shortage Follow-up Note

## 10.244. Bulk quantity below plan

Decision: if a bulk item is confirmed with quantity below the planned/required quantity, the system marks shortage and requires follow-up resolution.

Rules:
- confirmed quantity may be equal to required quantity;
- confirmed quantity may be less than required quantity;
- quantity above required quantity is not allowed;
- if confirmed quantity is less, create shortage mark for the row;
- shortage remains visible after final document confirmation;
- shortage requires later follow-up: find item, correct quantity, or complete formal removal/write-off process;
- extra items, if discovered separately, are handled manually outside the current document.

Purpose:
- keep documents tied to planned quantities;
- make missing bulk quantity visible;
- support later investigation without creating stock mix-ups.

MVP approach:
- store planned quantity;
- store confirmed quantity;
- if confirmed < planned, mark row as shortage;
- include shortage in document summary and internal follow-up list.
