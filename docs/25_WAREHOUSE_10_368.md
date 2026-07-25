# 25 Shortages 10.368

Decision: the long-press duration for opening the full-text tooltip follows the standard threshold provided by the device, operating system, browser, or interaction layer instead of using one fixed application-wide timeout.

Behavior:
- the application does not enforce a universal `500 ms` long-press threshold;
- native or framework-supported long-press semantics are preferred where available;
- the interaction should remain consistent with the user’s device expectations and accessibility settings;
- a normal short tap still performs no action according to decision 10.366;
- the tooltip opens only after the platform recognizes the gesture as a long press.

Architecture binding:
- gesture recognition belongs to the `apps/web` interaction layer;
- the threshold is not stored in the shortage domain and is not configurable per shortage;
- recognizing or cancelling the gesture invokes no shortage command;
- it creates no shortage history, audit event, notification, or other domain side effect.

MVP:
- use the standard long-press behavior available in the chosen browser or UI interaction implementation;
- do not hardcode a single cross-device duration unless required as a technical fallback;
- preserve the established short-tap and tooltip behavior from decisions 10.360–10.367.
