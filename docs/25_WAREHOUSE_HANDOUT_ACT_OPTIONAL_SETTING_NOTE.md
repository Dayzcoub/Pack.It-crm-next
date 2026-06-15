# 25 Warehouse — Handout Act Optional Setting Note

## 10.154. Handout act as an optional warehouse setting

Decision: the warehouse handout act should be controlled by a warehouse setting, not required for every handout by default.

Rules:
- small rental teams may work without a formal handout act;
- companies with stricter document flow can enable the handout act in settings;
- when enabled, the handout act becomes available in the warehouse handout process;
- when disabled, the warehouse can still use picking lists and internal handout tracking.

Purpose:
- keep the workflow flexible for small companies;
- avoid forcing unnecessary paperwork;
- support stricter companies that need formal warehouse documents.

MVP approach:
- add a warehouse setting for handout act usage;
- default can be off / optional;
- if enabled, allow generating handout act PDF/print from the warehouse handout operation;
- no prices should be included unless a separate later decision says otherwise.
