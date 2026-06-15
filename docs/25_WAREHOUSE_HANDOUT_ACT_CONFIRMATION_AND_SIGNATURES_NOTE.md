# 25 Warehouse — Handout Act Confirmation And Signatures Note

## 10.156. Confirmation and signatures in the handout act

Decision: the handout act should use system confirmation by default, with signatures kept as an optional setting.

Rules:
- by default, the act records who handed out the equipment;
- by default, the act records who received the equipment;
- date and time are stored automatically;
- manual signatures are not required by default;
- signatures can be enabled as an optional warehouse/document setting.

Optional signature mode:
- can be enabled by admin settings;
- may add signature fields to PDF/print forms;
- may support internal signature collection later if needed.

Purpose:
- keep the default workflow fast and practical;
- avoid forcing paperwork for small teams;
- still support companies that need stricter document confirmation.

MVP approach:
- system confirmation is enough for the default handout act;
- store user IDs and timestamps;
- add a configurable option for signature fields in generated documents.
