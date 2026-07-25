# 25 Shortages 10.354

Decision: long project or section names in the message about a shortage disappearing from the current list are truncated with an ellipsis.

Behavior:
- the message keeps the single-line format defined for project and section context;
- each long value may be visually truncated so that the message does not break the list layout;
- the full value is available through a tooltip or equivalent disclosure on pointer hover;
- the same full value is available when the truncated element receives keyboard focus;
- truncation changes only presentation and does not alter the underlying project or section name.

Architecture binding:
- truncation and full-text disclosure are `apps/web` presentation behavior;
- the source values come from the authoritative shortage projection and are not rewritten or persisted in shortened form;
- showing the tooltip creates no shortage history, audit event, side effect, or notification;
- assistive technologies must receive the complete value rather than only the visually truncated text.

MVP:
- long project and section values are rendered with an ellipsis when they exceed available space;
- full text is available on hover and keyboard focus;
- complete values remain accessible to screen readers;
- no shortened value is sent back to the server or stored as domain data.
