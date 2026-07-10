# 25 Warehouse 10.297

Decision: when an assigned user's proposal is accepted with an adjustment, the notification sent to that user must include both the corrected result and the mandatory reason for the change.

Example:
- assigned user proposes `found: 3`;
- warehouse keeper confirms `found: 2`;
- the assigned user receives a notification that the proposal was accepted with adjustment;
- the notification shows `found: 2` and the reason why the value was changed.

MVP:
- the notification clearly indicates that the proposal was accepted with adjustment;
- the corrected final result is shown in the notification;
- the required adjustment reason is shown in the same notification;
- the original proposal, corrected result, and reason remain available in the card history;
- if the corrected result closes only part of the shortage, the notification states that the shortage was partially closed and the remainder stays open.
