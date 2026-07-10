# 25 Warehouse 10.301

Decision: clicking `Accept proposal` opens a form prefilled with the assigned user's proposed result.

Behavior:
- if the confirmer saves the form without changing the proposed data, this is a normal proposal acceptance;
- if the confirmer changes allowed fields within the same result type, this is acceptance with adjustment;
- all validation rules for the selected result type remain active;
- when adjustment rules require it, the reason for the change is mandatory.

MVP:
- the form is prefilled from the original proposal;
- the confirmer can review all proposal data before saving;
- unchanged save creates a normal acceptance event;
- changed save creates an acceptance-with-adjustment event when the change is allowed by prior rules;
- history records the original proposal and the final confirmed result;
- the assigned user receives the corresponding acceptance notification.
