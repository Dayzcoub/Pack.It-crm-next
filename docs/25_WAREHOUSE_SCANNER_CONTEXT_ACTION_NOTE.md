# 25 Warehouse — Scanner Context Action Note

## 10.230. Scanner behavior depends on launch context

Decision: scanner behavior should depend on where the scanner was opened from. It should not always only open the item card by default.

Rules:
- if scanner is opened from inventory, scan performs inventory-related action;
- if scanner is opened from handout, scan performs handout-related action;
- if scanner is opened from return, scan performs return-related action;
- if scanner is opened from repair/problem workflow, scan performs the relevant repair/problem action;
- if scanner is opened from a generic warehouse view, it may open the item card;
- scanned code still resolves to the same stable item identity.

Purpose:
- reduce extra taps during operational workflows;
- make scanning fast on mobile;
- keep one scanner component with different context modes.

MVP approach:
- scanner receives context mode: inventory, handout, return, repair, generic;
- scan resolves item ID;
- context mode decides the next action or screen.
