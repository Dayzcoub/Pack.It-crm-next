# 25 Shortages 10.366

Decision: on touch devices, a normal short tap on a truncated project or section value does not open the full-text tooltip.

Behavior:
- the full value is opened only by the long-press interaction defined in decision 10.360;
- a short tap does not create a second activation path for the tooltip;
- a short tap does not change the current shortage state, list selection, filters, or recovery-mode state;
- if another interface action is assigned to the surrounding card or row, the truncated value must not introduce an unexpected competing tooltip action on short tap;
- keyboard focus and hover behavior on devices that support them remain governed by decision 10.354.

Architecture binding:
- recognizing short tap versus long press is transient `apps/web` interaction state;
- the interaction does not invoke `shortages.resolve`, `shortages.accept_proposal`, or any other domain command;
- it creates no shortage history, audit event, notification, or persisted preference.

MVP:
- short tap on a truncated value does nothing tooltip-specific;
- long press remains the only touch activation method for showing the full value;
- no domain or persistence side effects are produced.
