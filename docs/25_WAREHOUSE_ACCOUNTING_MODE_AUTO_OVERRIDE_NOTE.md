# 25 Warehouse — Accounting Mode Auto With Override Note

## 10.239. Individual/bulk mode assignment

Decision: system should suggest item accounting mode automatically by category/type, while allowing admin/director to override it manually.

Modes:
- individual — tracked and scanned one by one;
- bulk — confirmed by row/type and quantity.

Rules:
- system proposes mode based on item category/type;
- admin/director can override proposed mode in nomenclature/item settings;
- override should be saved and reused for future documents;
- category defaults can be adjusted later by company settings;
- item identity and marking mode remain independent from accounting mode.

Examples:
- speakers, consoles, radio systems, LED cabinets, cases: suggested individual;
- cables, adapters, consumables, small hardware: suggested bulk;
- admin/director can change any suggested mode when business logic requires it.

Purpose:
- reduce manual setup work;
- keep defaults practical;
- allow company-specific warehouse habits.

MVP approach:
- add automatic mode suggestion by category/type;
- add admin/director override field;
- use final selected mode in scan/progress behavior.
