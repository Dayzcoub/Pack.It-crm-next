# 25 Shortages 10.364

Decision: if a tooltip with the full value is open and a container resize makes the source value fully visible without truncation, the tooltip closes automatically.

Behavior:
- container width and truncation state are recalculated after layout changes;
- if the source project or section value is no longer truncated, its open tooltip closes automatically;
- if the value remains truncated, the tooltip may remain open unless another established close condition occurs;
- automatic closing does not move focus unexpectedly or trigger another shortage action;
- the displayed project and section values continue to follow decisions 10.349–10.359.

Architecture binding:
- tooltip visibility and text truncation are transient `apps/web` presentation state;
- the behavior does not invoke `shortages.resolve`, `shortages.accept_proposal`, or any other application command;
- no shortage history, audit event, notification, or server-side state is created;
- the full value continues to come from the existing shortage read projection.

MVP:
- observe the actual source element after container width changes;
- automatically close the tooltip when the source text becomes fully visible;
- preserve the tooltip while the source remains truncated, subject to the other established close rules;
- no domain or persistence side effects are produced.
