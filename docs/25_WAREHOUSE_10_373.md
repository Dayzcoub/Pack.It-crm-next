# 25 Shortages 10.373

Decision: if the full tooltip text does not fit within the viewport height, the text remains inside the tooltip and the page may be scrolled without closing that tooltip.

Behavior:
- the tooltip still renders the complete text without its own internal height limit according to decision 10.372;
- no separate full-screen panel is opened;
- when the tooltip is taller than the available viewport, normal page scrolling is allowed so the user can read the remaining content;
- for this exceptional overflow case, scrolling does not close the tooltip;
- this rule is an explicit exception to decision 10.362, which closes ordinary tooltips when scrolling begins;
- the tooltip remains open until one of the other defined close conditions occurs, such as tapping outside it or the source value becoming fully visible.

Architecture binding:
- overflow detection and temporary scroll behavior are presentation concerns owned by `apps/web`;
- the component determines the exception from the rendered tooltip and viewport geometry;
- the tooltip content remains derived from the existing read projection;
- the behavior invokes no shortage command and creates no shortage history, audit event, or notification.

MVP:
- oversized tooltip content remains fully available;
- page scrolling is enabled for reading it;
- the tooltip is not converted into a separate panel and has no internal scrollbar;
- scrolling closes ordinary tooltips but not tooltips that exceed the viewport height.
