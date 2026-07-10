# 25 Warehouse 10.302

Decision: the `Adjustment reason` field appears only after the confirmer changes proposal data in the prefilled acceptance form.

Behavior:
- while all proposal data remains unchanged, the field is hidden;
- after any allowed proposal value is changed, the field appears;
- once shown, the field is mandatory before the adjusted acceptance can be saved;
- if there is no data change, the action remains a normal proposal acceptance and no adjustment reason is required.

MVP:
- the form compares current values with the original proposal;
- the adjustment field is shown only when a meaningful difference exists;
- adjusted acceptance cannot be submitted with an empty adjustment reason;
- the entered reason is stored in history and included in the notification to the assigned user;
- unchanged acceptance preserves the simpler form without an unnecessary reason field.
