# 25 Shortages 10.297

Decision: when an assigned user's proposal is accepted with an adjustment, the notification sent to that user must include both the corrected result and the mandatory reason for the change.

Architecture binding:
- `shortages` owns the accepted result, adjustment reason, and domain history;
- after a successful transaction, `shortages` produces an acceptance-with-adjustment event;
- `notifications` delivers the message and does not decide or modify the shortage result;
- `audit` records the significant action separately.

Example:
- assigned user proposes `found: 3`;
- an authorized confirmer confirms `found: 2`;
- the assigned user receives a notification that the proposal was accepted with adjustment;
- the notification shows `found: 2` and the reason why the value was changed.

MVP:
- the notification clearly indicates acceptance with adjustment;
- the corrected final result is shown;
- the required adjustment reason is shown in the same notification;
- the original proposal, corrected result, and reason remain available in shortage domain history;
- if the result closes only part of the shortage, the notification states that the shortage was partially closed and the remainder stays open;
- notification delivery failure does not roll back an already committed shortage decision and must follow the configured retry/outbox policy.