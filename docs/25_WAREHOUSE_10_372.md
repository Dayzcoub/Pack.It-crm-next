# 25 Shortages 10.372

Decision: the tooltip for a very long value shows the complete text without limiting its own height and without an internal scroll area.

Behavior:
- the tooltip wraps the full value across as many lines as needed;
- the tooltip does not truncate the displayed full text;
- the tooltip does not introduce an independent internal scrollbar;
- the tooltip grows with its content within the available viewport;
- page-level positioning may adjust so the tooltip remains visible as far as the viewport allows;
- ordinary closing rules from decisions 10.361–10.365 continue to apply.

Architecture binding:
- this is transient presentation behavior owned by `apps/web`;
- the tooltip renders the already available user-facing value and does not request or derive additional shortage data;
- opening, resizing, repositioning, or closing the tooltip invokes no shortage command;
- it creates no shortage history, audit event, or notification.

MVP:
- the full text is displayed without an internal height cap;
- no internal tooltip scrolling is used;
- multiline wrapping preserves the complete value;
- the tooltip follows the established close and replacement rules.
