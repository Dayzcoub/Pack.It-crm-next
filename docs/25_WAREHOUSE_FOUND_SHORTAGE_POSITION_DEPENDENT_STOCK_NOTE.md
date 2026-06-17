# 25 Warehouse — Found Shortage Position-dependent Stock Note

## 10.255. Found shortage stock recovery depends on item position

Decision: when shortage is closed with found result, stock recovery behavior depends on the specific item/position and its accounting rules.

Rules:
- there is no single universal automatic stock recovery rule for all bulk positions;
- behavior depends on the item/position type and accounting mode;
- for some positions, found quantity may restore available stock automatically;
- for other positions, warehouse keeper must manually confirm or adjust quantity;
- decision should respect item settings and audit requirements;
- closure history must show whether stock quantity was restored automatically or manually.

Purpose:
- avoid wrong stock changes for different categories of items;
- support both simple bulk items and more sensitive/controlled positions;
- keep quantity corrections auditable.

MVP approach:
- add item/position-level handling rule for found shortages;
- possible modes: auto restore, require manual quantity confirmation;
- record actual applied stock change in shortage history.
