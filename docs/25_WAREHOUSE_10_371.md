# 25 Shortages 10.371

Decision: for a truncated shortage context value, the system text-selection and native context-menu behavior is suppressed so that a long press opens only the application tooltip with the full value.

Behavior:
- the rule applies only to truncated project and section values that support the full-text tooltip;
- a successful long press opens the application tooltip according to decisions 10.360–10.370;
- the browser or operating-system selection handles and native context menu are not shown for this interaction;
- ordinary short press remains inactive according to decision 10.366;
- text inside the opened tooltip may be selected and copied through the platform's standard behavior;
- other text in the interface keeps its normal selection and context-menu behavior.

Architecture binding:
- suppression is local presentation behavior owned by `apps/web`;
- it must be scoped to the interactive truncated-value element and must not disable selection globally;
- the behavior invokes no shortage command and creates no shortage history, audit event, or notification.

MVP:
- a long press on a truncated value opens only the application tooltip;
- native selection and context menus do not compete with the gesture;
- full tooltip text remains available for normal selection and copying;
- unrelated interface text keeps standard platform behavior.
