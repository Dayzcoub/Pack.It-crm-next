# 25 Warehouse 10.303

Decision: if the confirmer changes proposal data, then restores every value to the original proposal, the action returns to normal proposal acceptance.

Behavior:
- while changed values differ from the original proposal, the `Adjustment reason` field is visible and required;
- when all values again match the original proposal, the field is hidden;
- any text entered in the adjustment reason field is cleared;
- saving the unchanged form creates a normal proposal acceptance, not acceptance with adjustment.

MVP:
- the form continuously compares current values with the original proposal;
- adjustment state ends only when all meaningful values match the original proposal again;
- stale adjustment text is not retained after returning to the original values;
- history records a normal acceptance event when the restored form is saved;
- the assigned user receives the normal proposal-accepted notification.
