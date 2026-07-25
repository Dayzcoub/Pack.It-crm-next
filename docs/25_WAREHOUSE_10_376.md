# 25 Shortages 10.376

Decision: the full-value window does not include a separate `Закрыть` button.

Behavior:
- the window is opened by ordinary activation of a truncated project or section value according to decisions 10.374 and 10.375;
- the user closes it by activating the area outside the window;
- on devices and environments that provide a system or browser Back action, that action also closes the window;
- closing the window does not trigger any shortage command or modify shortage data;
- the originating truncated value remains the logical return target after closing.

Accessibility:
- keyboard users can close the window with the standard Escape action where supported;
- after closing, focus returns to the value that opened the window;
- assistive technologies receive the window semantics and its selected field label.

Architecture binding:
- this is transient presentation behavior owned by `apps/web`;
- no domain state, shortage history, audit event, or notification is created;
- decisions 10.360–10.373 remain superseded by decision 10.374.

MVP:
- no dedicated close button is rendered;
- outside activation and the standard Back or Escape action close the window;
- focus returns to the originating value.
