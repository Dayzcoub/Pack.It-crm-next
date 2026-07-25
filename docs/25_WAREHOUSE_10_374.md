# 25 Shortages 10.374

Decision: simplify access to the full text of truncated project and section values on touch devices. A normal tap opens a standard overlay window with the full text. Decisions 10.360–10.373 are superseded by this rule.

Behavior:
- on pointer devices, the full value remains available on hover and keyboard focus according to decision 10.354;
- on touch devices, a normal tap on a truncated value opens a standard overlay window or panel with the full value;
- no long-press gesture is required;
- no custom haptic feedback, movement threshold, suppressed system context menu, or special long-press timing is used;
- the window closes by tapping outside it or through the platform-standard back or close action;
- long text is displayed in the standard scrollable content area of the window when necessary;
- only one full-text window may be open at a time;
- tapping another truncated value replaces the displayed content with that value.

Supersession:
- decisions 10.360–10.373 remain in the repository as decision history;
- their long-press tooltip behavior is no longer normative;
- implementation and acceptance criteria must follow this decision when those earlier notes conflict with it.

Architecture binding:
- this is presentation behavior owned by `apps/web`;
- the overlay receives the value already present in the shortage read projection;
- opening or closing it invokes no shortage command;
- it creates no shortage history, audit event, or notification;
- the component should use the existing standard dialog, sheet, or equivalent overlay primitive of the design system rather than a custom gesture subsystem.

MVP:
- truncated values are opened by a normal tap on touch devices;
- desktop hover and keyboard-focus access remain available;
- long-press-specific behavior is not implemented;
- decisions 10.360–10.373 are treated as superseded.
