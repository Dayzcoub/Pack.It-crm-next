# 25 Shortages 10.324

Decision: if the next invalid field is outside the visible area of the form, the form automatically scrolls to that field and moves focus to it.

Behavior:
- automatic navigation is triggered after the current invalid field becomes valid and another invalid field remains;
- if the next invalid field is outside the current viewport, the form scrolls until the field and its error message are visible;
- focus is then placed on that invalid field;
- all entered form data remains unchanged;
- the behavior applies to the shortage resolution form owned by the `shortages` context.

MVP:
- automatic scrolling and focus movement work as one navigation action;
- the field is not obscured by a sticky header or footer after scrolling;
- the user can immediately edit the next invalid field;
- no shortage action is submitted until all server-required fields pass validation;
- this client-side navigation does not replace server-side validation in the `shortages.resolve` or `shortages.accept_proposal` use case.
