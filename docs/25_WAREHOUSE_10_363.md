# 25 Shortages 10.363

Decision: if a full-text tooltip is already open and the user long-presses another truncated value, the current tooltip is replaced by the tooltip for the newly selected value.

Behavior:
- only one full-text tooltip may be open at a time;
- a successful long press on another truncated project or section value closes the previous tooltip and opens the new one as a single interaction;
- the user is not required to dismiss the previous tooltip separately;
- the new tooltip is anchored to the newly selected value;
- the tooltip remains open until the user taps outside it or another closing condition from the related decisions occurs;
- replacing the tooltip does not modify the underlying shortage data or current list state.

Accessibility:
- assistive technologies are informed that the displayed full text has changed;
- focus and semantic association move to the newly selected value without leaving two simultaneously active descriptions;
- the full value remains available independently of visual truncation.

Architecture binding:
- the open tooltip and its anchor are transient `apps/web` presentation state;
- changing the active tooltip does not invoke a shortage command;
- it creates no shortage history, audit event, notification, or other domain side effect.

MVP:
- only one tooltip is displayed at a time;
- long-pressing another truncated value replaces the current tooltip immediately;
- the new tooltip shows the full text of the newly selected value;
- no server-side state is created or changed.
