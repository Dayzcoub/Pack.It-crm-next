# 25 Shortages 10.380

Decision: when a muted full-value popup is already open, tapping another truncated value immediately replaces the popup content and repositions it near the new tap point.

Behavior:
- the existing popup is reused rather than closed and reopened as a separate interaction;
- the displayed value changes to the newly selected project or section value;
- the popup anchor and placement are recalculated from the new tap point;
- viewport collision handling continues to keep the popup within visible screen bounds;
- no confirmation or transition step is required;
- only one muted full-value popup may be visible at a time.

Architecture binding:
- this is transient `apps/web` presentation state;
- changing the displayed popup value invokes no shortage command and creates no shortage history, audit event, or notification.

MVP:
- tapping another truncated value updates the existing popup immediately;
- the popup moves to the new tap location;
- duplicate popups are not created.
