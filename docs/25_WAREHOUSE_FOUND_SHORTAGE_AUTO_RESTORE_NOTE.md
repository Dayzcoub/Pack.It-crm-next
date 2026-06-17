# 25 Warehouse — Found Shortage Auto Restore Note

## 10.256. Found shortage automatically restores available quantity

Decision: when shortage is closed with found result, the found quantity should automatically return to available stock.

Rules:
- closing result found restores missing quantity automatically;
- no separate manual quantity confirmation is required;
- restored quantity must match the shortage missing quantity or the explicitly found quantity if partial found closure is later supported;
- stock movement/change is logged;
- shortage closure history shows that quantity was restored automatically;
- warehouse keeper and responsible person can see the closure result in history.

Purpose:
- reduce manual work for simple found shortages;
- keep warehouse summary clean after found items are confirmed;
- preserve audit trail for automatic stock restoration.

MVP approach:
- close shortage as found;
- system adds missing quantity back to available bulk stock;
- system closes shortage entry;
- system records actor, time, source project, and restored quantity.
