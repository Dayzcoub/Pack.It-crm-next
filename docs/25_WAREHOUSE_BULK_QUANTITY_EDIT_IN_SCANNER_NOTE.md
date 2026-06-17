# 25 Warehouse — Bulk Quantity Edit in Scanner Note

## 10.241. Bulk quantity correction location

Decision: for bulk items, quantity can be edited directly on the scanner screen.

Rules:
- bulk scan opens/uses an inline quantity control on the scanner screen;
- default quantity is the required quantity;
- user can adjust quantity without leaving the scanner;
- adjusted quantity is used in current staged list and progress counter;
- user can continue scanning after quantity correction.

Purpose:
- avoid extra navigation;
- keep mobile scanning fast;
- make bulk item correction convenient during handout, return, and inventory workflows.

MVP approach:
- after bulk row scan, show compact quantity field/stepper;
- prefill required quantity;
- allow immediate correction;
- save corrected quantity into current scan context.
