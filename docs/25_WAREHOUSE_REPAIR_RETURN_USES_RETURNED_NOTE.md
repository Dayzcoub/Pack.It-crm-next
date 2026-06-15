# 25 Warehouse — Repair Return Uses Returned Note

## 10.216. Status for item returned from repair and awaiting check

Decision: do not add a separate check_required status for MVP. Use returned with a note/comment that the item came back from repair and requires checking.

Rules:
- item returning from repair moves to returned, not directly to available;
- add a marker/comment such as returned from repair, requires check;
- technician checks the item;
- if OK, technician moves it to available;
- if not OK, technician moves it back to in_repair or service center workflow;
- returned remains conditionally available and requires confirmation before available.

Purpose:
- avoid status list bloat for MVP;
- keep the repair return workflow understandable;
- preserve the check step before the item returns to active stock.

MVP approach:
- reuse returned status;
- add repair-return/check-needed context as comment or flag;
- log all transitions with user, date, time, and source context.
