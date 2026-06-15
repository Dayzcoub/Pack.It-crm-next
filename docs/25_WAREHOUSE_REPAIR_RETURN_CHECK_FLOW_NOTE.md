# 25 Warehouse — Repair Return Check Flow Note

## 10.215. Item return flow after repair

Decision: an item returning from repair should not move directly to available. It should first move to returned / check state, then a technician verifies it.

Rules:
- after repair, item first receives returned or check-required state;
- technician checks the item;
- if everything is OK, technician moves the item back to available;
- if the item is still not OK, technician sends it back to in_repair or to service center;
- direct in_repair -> available transition should not be the default workflow;
- all transitions must be logged with user, date, time, item, and comment where applicable.

Purpose:
- prevent unverified repaired equipment from returning to active stock;
- make the technician responsible for final operational check;
- keep repair loops traceable if the item has to go back to repair/service.

MVP approach:
- model repair return as in_repair -> returned/check -> available or in_repair/service;
- require technician/user with proper warehouse change permission for the final check transition;
- keep in_repair and check-required states unavailable until confirmed.
