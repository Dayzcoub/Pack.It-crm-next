# 25 Shortages 10.367

Decision: shortened project and section values do not receive a separate visual indicator for the long-press action.

Behavior:
- an ellipsis remains the only visible sign that a value is shortened;
- no icon, underline, badge, helper text, or other long-press hint is added;
- on touch devices, the full value remains available through the long-press interaction defined in decision 10.360;
- a normal short press continues to have no effect according to decision 10.366;
- desktop access through hover and keyboard focus remains unchanged.

Architecture binding:
- the absence of a visible indicator is an `apps/web` presentation rule;
- it does not change the shortage read projection or source data;
- displaying the full value remains a transient interface action;
- it creates no shortage history, audit event, notification, or other domain side effect.

MVP:
- do not add a separate visual long-press indicator;
- keep ellipsis for shortened values;
- preserve long press, hover, focus, and assistive-technology access to the full value;
- do not invoke a shortage command from any full-text preview interaction.
