# 25 Shortages 10.379

Decision: the muted full-value popover is positioned next to the point where the user tapped the truncated value.

Behavior:
- the popover opens beside the selected project or section value;
- positioning uses the actual tap target as its visual anchor;
- if there is not enough space in the preferred direction, the popover shifts or flips to remain within the visible viewport;
- the popover must not cover the tapped value when another valid placement is available;
- the popover remains non-modal and does not block the rest of the interface;
- scrolling closes the popover according to decision 10.378.

Architecture binding:
- placement and viewport collision handling are transient `apps/web` presentation behavior;
- opening, repositioning, or closing the popover invokes no shortage command;
- no shortage history, audit event, or notification is created.

MVP:
- open the muted popover near the tapped value;
- keep it inside the viewport through automatic placement adjustment;
- preserve the non-modal behavior established in decisions 10.374–10.378.
