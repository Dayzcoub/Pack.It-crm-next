# 25 Shortages 10.362

Decision: an open full-text tooltip is closed as soon as page or containing-area scrolling begins.

Behavior:
- the rule applies to a tooltip opened by long press on a truncated project or section value;
- scrolling the page, shortage list, modal content, or another scrollable ancestor closes the tooltip;
- the tooltip is dismissed at the start of the scroll gesture rather than after scrolling ends;
- the underlying list and scroll interaction continue normally;
- closing the tooltip does not change selection, filters, shortage state, or the displayed truncated value;
- the user may open the tooltip again with another long press after scrolling stops.

Rationale:
- a tooltip must not remain visually detached from the value that opened it;
- immediate dismissal prevents stale overlays from covering newly visible content;
- the behavior is consistent with decision 10.361, where the tooltip otherwise remains open until an explicit outside interaction.

Architecture binding:
- the tooltip and its dismissal are transient `apps/web` presentation state;
- scroll detection is handled by the presentation layer and does not invoke a shortage command;
- dismissing the tooltip creates no shortage history, audit event, notification, or other domain side effect.

MVP:
- any relevant scroll start closes the open tooltip;
- scrolling is not blocked or delayed;
- no domain or persistence action is performed;
- the tooltip can be opened again after scrolling.
