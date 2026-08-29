# 25 Shortages 10.399

Decision: when one proposal is accepted as the final resolution for a shortage, authors of the other active proposals that are automatically closed as no longer relevant receive a notification.

Behavior:
- accepting the final resolution closes the remaining active proposals for the same shortage according to decision 10.398;
- each affected proposal author is notified that another final resolution was accepted for the shortage;
- the notification makes clear that their proposal was closed as no longer relevant rather than rejected on its own merits;
- closed proposals remain available in shortage history;
- no additional user action is required from proposal authors.

Architecture binding:
- `shortages` owns the proposal state transitions and shortage history;
- `notifications` delivers notifications only after the final resolution and automatic proposal closures succeed;
- notification delivery does not own or alter shortage state;
- `audit` may independently record the final resolution and resulting proposal closures according to audit policy.

MVP:
- other active proposals are automatically closed after one final resolution is accepted;
- their authors receive a notification that another final resolution was chosen;
- all proposal records remain in history.
