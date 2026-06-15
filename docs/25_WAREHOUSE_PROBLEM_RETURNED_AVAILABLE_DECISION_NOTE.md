# 25 Warehouse — Problem Return to Available Decision Note

## 10.210. Returning problematic items to available status

Decision: if a returned item has a problem row, moving it back to available is left to the receiving user's judgement, depending on the problem type.

Rules:
- do not always block returned -> available when a problem row exists;
- the receiving user evaluates the problem type and item condition;
- if the problem is damage, malfunction, or safety/working-condition related, the item should wait for a resolution before becoming available;
- if the problem is about completeness, documentation, accessory shortage, or similar non-blocking issues, the item may be returned to available when the receiver decides it is acceptable;
- the system should warn the user that a problem row exists before allowing available status;
- the transition must be logged with user, date, time, problem row, and comment if provided.

Purpose:
- avoid blocking usable equipment unnecessarily;
- keep unsafe or non-working equipment out of active stock;
- let the receiving warehouse/technical user make a practical decision based on the actual problem.

MVP approach:
- show a warning when returning problematic items to available;
- allow the receiver to confirm available when appropriate;
- require resolution first for clearly blocking problem categories such as damaged or not working, where possible;
- keep all transitions auditable.
