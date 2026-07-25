# 25 Shortages 10.378

Decision: the muted full-value popover closes when page scrolling begins.

Behavior:
- the popover is transient and remains visually associated with the value that opened it;
- any intentional page scroll closes the popover immediately;
- after closing, the user may reopen it by tapping the truncated value again;
- the popover does not follow the source value during scrolling;
- this rule confirms the previously established scroll-close behavior for the simplified interaction introduced in decisions 10.374–10.377.

Architecture binding:
- this is transient `apps/web` presentation behavior;
- closing the popover performs no shortage command and creates no shortage history, audit event, or notification.

MVP:
- opening the popover does not block the interface;
- starting page scroll closes it;
- reopening requires a new tap on a truncated value.
