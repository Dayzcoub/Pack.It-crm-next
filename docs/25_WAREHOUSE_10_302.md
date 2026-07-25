# 25 Shortages 10.302

Decision: the `Adjustment reason` field appears only after the confirmer changes proposal data in the prefilled acceptance form.

Architecture binding:
- UI visibility is derived from the difference between the form and original shortage proposal;
- mandatory validation is enforced by the `shortages` application use case, not only by the client;
- submission requires `shortages.accept_proposal` within the applicable scope.

Behavior:
- while all proposal data remains unchanged, the field is hidden;
- after any allowed proposal value is changed, the field appears;
- once shown, the field is mandatory before the adjusted acceptance can be saved;
- if there is no data change, the action remains a normal proposal acceptance and no adjustment reason is required.

MVP:
- the form compares current values with the original proposal;
- the adjustment field is shown only when a meaningful difference exists;
- adjusted acceptance cannot be submitted with an empty adjustment reason;
- the entered reason is stored in shortage domain history;
- after successful commit, `notifications` includes the reason in the message to the assigned user;
- unchanged acceptance preserves the simpler form without an unnecessary reason field.