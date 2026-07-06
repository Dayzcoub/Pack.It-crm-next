# 25 Warehouse — Shortage Responsible Change Old Notification Note

## 10.276. Notify old responsible person when reassigned

Decision: when shortage responsible person is changed, the previous responsible person should also receive a notification that the shortage was removed from them.

Rules:
- new responsible person receives assignment notification;
- previous responsible person receives removal/reassignment notification;
- notification should be sent only if there was a previous responsible person;
- notification should include source project, missing item/row, missing quantity, and current status;
- notification opens the shortage detail card or related history view;
- reassignment event is logged in shortage action history with actor and timestamp.

Purpose:
- make ownership changes clear;
- prevent old responsible person from continuing unnecessary follow-up;
- preserve accountability for reassignment.

MVP approach:
- on responsible change, create two notification events where applicable: assigned to new user and removed from old user;
- store reassignment action in shortage history.
