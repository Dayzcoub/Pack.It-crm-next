# 25 Shortages 10.394

Decision: when an administrator forcibly releases another user's shortage-proposal editing lock, the affected user receives a separate notification explaining that the lock was released by an administrator and showing the administrator-provided reason.

Behavior:
- the notification identifies that the lock was forcibly released by an administrator;
- the notification includes the reason entered for the forced release;
- the affected user's open form follows decision 10.392 and becomes read-only while preserving the values currently visible on screen;
- the user may later attempt to acquire a new lock if the proposal is still available for editing;
- notification delivery occurs only after the forced lock release succeeds.

Architecture binding:
- lock ownership and release are application coordination for the `shortages` workflow;
- the forced-release action is recorded separately by `audit` according to decision 10.393;
- `notifications` delivers the post-action notification and does not own lock state;
- no shortage resolution, proposal acceptance, inventory correction, writeoff, or subrent side effect is created by the notification itself.

MVP:
- successful forced release triggers a notification to the displaced user;
- the notification states that an administrator released the lock and displays the entered reason;
- the displaced user's form becomes read-only and keeps its visible values.
