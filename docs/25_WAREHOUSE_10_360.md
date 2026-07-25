# 25 Shortages 10.360

Decision: on touch devices, the full text of a truncated project or section value opens after a long press on that value.

Behavior:
- the long-press interaction applies only when the displayed value is actually truncated;
- the tooltip or compact overlay shows the complete value without changing the shortage list layout;
- a normal short tap does not open the full-text overlay and remains available for the row's primary interaction;
- the interaction must not trigger the browser context menu or text selection instead of the product behavior;
- keyboard focus and pointer hover continue to reveal the same full text on devices that support them;
- assistive technologies receive the complete accessible name without requiring the long-press gesture.

Architecture binding:
- the complete project or section name comes from the same shortage read projection as the truncated visible value;
- opening or closing the full-text overlay is transient `apps/web` state;
- the interaction does not invoke a shortage command;
- it creates no shortage history, audit event, notification, or other domain side effect.

MVP:
- a long press on a truncated value opens its complete text;
- a short tap preserves the normal row interaction;
- non-truncated values do not need the long-press overlay;
- the complete value remains available to keyboard and assistive-technology users.
