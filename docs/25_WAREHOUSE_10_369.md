# 25 Shortages 10.369

Decision: opening the full-text tooltip by long press is cancelled when finger movement exceeds the system gesture-recognition threshold.

Behavior:
- the interaction uses the platform or browser movement tolerance associated with long-press recognition;
- movement within the allowed tolerance does not cancel the long press;
- movement beyond the threshold cancels tooltip opening and allows the intended scroll, drag, or other gesture to continue;
- after cancellation, releasing the finger does not open the tooltip;
- a new long press is required for another attempt.

Architecture binding:
- gesture recognition and cancellation remain transient `apps/web` interaction state;
- no custom business rule or shortage command depends on the gesture threshold;
- cancellation creates no shortage history, audit event, notification, or other domain side effect.

MVP:
- respect the system or browser movement threshold;
- cancel pending tooltip opening when the threshold is exceeded;
- do not interfere with normal scrolling;
- require a new long press after cancellation.
