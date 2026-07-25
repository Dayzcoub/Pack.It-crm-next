# 25 Shortages 10.386

Decision: when a responsible person withdraws a previously submitted shortage resolution proposal, the warehouse role receives a separate notification.

Behavior:
- the notification is created only after the proposal withdrawal succeeds;
- the notification identifies the affected shortage and indicates that the previously submitted proposal is no longer active;
- the shortage remains open and available for further resolution;
- the withdrawn proposal remains visible in shortage history with its withdrawn status;
- the notification does not itself change the shortage state or create a replacement proposal.

Architecture binding:
- `shortages` owns the proposal withdrawal command, proposal status, and shortage history entry;
- `notifications` delivers the warehouse notification only after the source action has completed successfully;
- `audit` records the significant withdrawal action separately;
- failed or rolled-back withdrawal attempts create no notification.

MVP:
- a successful proposal withdrawal creates one warehouse notification;
- the notification clearly distinguishes withdrawal from rejection or final resolution;
- duplicate delivery is prevented for the same successful withdrawal event.
