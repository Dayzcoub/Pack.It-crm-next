# 25 Shortages 10.383

Decision: repeated activation of the same truncated value does not close or recreate the muted popover.

Behavior:
- if the popover is already open for the selected project or section value, another activation of that same value leaves it open;
- its content and position remain unchanged;
- no additional animation, timer reset, focus reset, or duplicate popover is triggered;
- the popover still closes through the established outside activation, page scrolling, or system Back action;
- activation of a different truncated value remains governed by decision 10.380.

Architecture binding:
- this is transient `apps/web` presentation behavior;
- repeated activation invokes no shortage command and creates no shortage history, audit event, or notification.

MVP:
- repeated activation of the same source is idempotent;
- only one muted popover may be open at a time;
- the existing popover remains stable until another established close or replacement action occurs.
