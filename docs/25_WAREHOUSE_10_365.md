# 25 Shortages 10.365

Decision: if a tooltip was automatically closed because the container became wide enough to show the full value, narrowing the container again does not reopen the tooltip automatically.

Behavior:
- when the container becomes wide enough and the value is no longer truncated, the open tooltip closes according to decision 10.364;
- if the container later narrows and the value becomes truncated again, only the shortened value is shown;
- the tooltip opens again only after a new explicit user action, including a long press on a touch device;
- the interface does not restore the previous tooltip state after responsive layout changes;
- this prevents unexpected overlays from appearing without a current user request.

Architecture binding:
- tooltip visibility and truncation state belong to transient `apps/web` presentation state;
- container size changes do not invoke a shortage command;
- no tooltip state is persisted in the shortage domain or restored after page reload;
- automatic closing and the absence of automatic reopening create no shortage history, audit event, notification, or other domain side effect.

MVP:
- a tooltip closes when its full value becomes visible;
- later truncation does not reopen it automatically;
- the user must invoke the tooltip again explicitly;
- responsive layout changes do not create domain side effects.
