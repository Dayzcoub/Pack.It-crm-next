# 25 Warehouse — In Repair Visible but Unavailable Note

## 10.217. Visibility and availability of items in repair

Decision: an item in in_repair status must remain in warehouse accounting, but it is not available for projects while it is in repair.

Rules:
- in_repair items are unavailable for booking/reservation/project use;
- in_repair items should not be hidden from warehouse accounting;
- stock views should distinguish available stock from unavailable/in-repair stock;
- project availability calculations must exclude in_repair items;
- warehouse users should still be able to find and track in_repair items.

Purpose:
- keep real stock accounting complete;
- prevent equipment in repair from being selected for projects;
- keep repair items traceable until they return and pass checking.

MVP approach:
- count in_repair items in total inventory context;
- exclude in_repair items from available quantity;
- show them as unavailable / in repair in warehouse views where relevant.
