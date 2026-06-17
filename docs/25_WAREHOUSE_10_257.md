# 25 Warehouse — 10.257

Decision: partial found quantity is allowed.

Rules:
- if only part of the shortage is found, that found quantity is returned to available stock automatically;
- the remaining quantity stays open;
- the record keeps original quantity, found quantity, and remaining quantity;
- each partial action is logged;
- the shortage closes only when the remaining quantity becomes zero or another final resolution is applied.

MVP:
- allow entering found quantity;
- restore that quantity automatically;
- keep the rest in the warehouse keeper open summary.
