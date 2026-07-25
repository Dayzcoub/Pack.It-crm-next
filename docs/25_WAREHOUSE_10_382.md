# 25 Shortages 10.382

Decision: the muted full-value popover does not close automatically on a timer.

Behavior:
- the popover remains open until the user performs an explicit closing action;
- supported closing actions are tapping outside the popover, beginning page scrolling, or using the system Back action;
- text selection or copying inside the popover does not start or reset any timeout because no timeout exists;
- moving the popover to another truncated value follows decision 10.380 and does not introduce automatic dismissal.

Architecture binding:
- popover lifetime is transient `apps/web` interaction state;
- no shortage command is invoked and no shortage history, audit event, or notification is created;
- the interface must not depend on a hidden countdown for access to the full value.

MVP:
- no auto-dismiss timer;
- explicit outside tap, scroll, or Back closes the popover;
- the popover remains available long enough for reading, selection, and copying.
