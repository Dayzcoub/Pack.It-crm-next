# 25 Shortages 10.356

Decision: if one context value is short, the other value may use the released width.

Behavior:
- the context line keeps the format `Проект: … | Раздел: …`;
- equal width remains the baseline when both values require truncation;
- if one value fits within less than its baseline share, the unused width is reassigned to the other value;
- project and section values are truncated independently with an ellipsis only when their final available width is insufficient;
- full values remain available on hover and keyboard focus according to the long-name display rule.

Architecture binding:
- width redistribution is presentation logic in `apps/web`;
- it does not change project, section, or shortage data;
- it does not invoke a source-domain command and creates no shortage history, audit event, side effect, or notification;
- the displayed project and section values come from the current server projection used for the conflict message.

MVP:
- begin with an equal-width allocation for project and section;
- allow either value to consume unused width from the other;
- keep the explicit labels and vertical separator visible;
- truncate only the value that still exceeds its final allocated width;
- expose the complete truncated value on hover and focus.
