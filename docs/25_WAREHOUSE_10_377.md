# 25 Shortages 10.377

Decision: the full value is shown in a non-modal muted popover rather than in a blocking dialog.

Behavior:
- tapping a truncated value opens a small contextual popover near the selected value;
- the popover shows only the selected full value according to decision 10.375;
- the rest of the interface remains visible and usable;
- no backdrop, focus trap, or page-level blocking is applied;
- the visual treatment is intentionally muted and subordinate to the main shortage interface;
- the popover closes when the user taps outside it or invokes the system Back action according to decision 10.376;
- opening the popover does not navigate away from the shortage list and does not change shortage state.

Architecture binding:
- this is transient presentation state owned by `apps/web`;
- the popover is anchored to the rendered truncated value and is not represented in domain data or read projections;
- it invokes no shortage command and creates no shortage history, audit event, or notification.

MVP:
- use a non-modal contextual popover;
- keep the surrounding interface interactive;
- use a muted visual style without a blocking backdrop;
- show only the selected full value.
