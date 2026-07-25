# 25 Shortages 10.358

Decision: the project-and-section context switches from one line to two lines according to the actual available width of its container and the readability of the displayed values, rather than according to a fixed viewport breakpoint.

Behavior:
- the default layout remains one line: `Проект: … | Раздел: …`;
- the component evaluates the width available inside its own container;
- when both labelled values cannot remain sufficiently readable in one line, the component switches to two lines;
- the layout must work consistently in a full page, narrow column, modal window, drawer, or other embedding context;
- resizing or changing the containing layout may move the component between one-line and two-line modes without reloading the page;
- the transition does not depend solely on the width of the browser window.

Implementation guidance:
- prefer container-aware responsive layout, such as CSS container queries, flex/grid constraints, or an equivalent component-local mechanism;
- use a defined minimum readable width for each labelled value instead of an arbitrary global screen breakpoint;
- avoid JavaScript text measurement when the same behavior can be expressed reliably through CSS layout rules;
- truncation and full-text access continue to follow decision 10.354.

Architecture binding:
- the responsive mode is transient `apps/web` presentation state;
- the project and section values come from the existing shortage read projection;
- switching layout modes does not invoke a shortage command;
- it creates no shortage history, audit event, notification, or other domain side effect.

MVP:
- the context component responds to its own available width;
- it uses one line when both values remain readable;
- it switches to two lines when the container becomes too narrow;
- no fixed viewport-only breakpoint determines this behavior.
