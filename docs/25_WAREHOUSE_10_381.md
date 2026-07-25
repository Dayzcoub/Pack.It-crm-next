# 25 Shortages 10.381

Decision: full text inside the muted popup may be selected and copied using the platform's standard text-selection behavior.

Behavior:
- the popup remains non-modal and read-only;
- users may select part or all of the displayed project or section value;
- standard copy actions provided by the browser or operating system remain available;
- selecting text inside the popup does not close it;
- clicking or tapping outside, scrolling, or invoking the system Back action closes it according to the existing rules;
- no separate Copy button is required.

Architecture binding:
- text selection and clipboard interaction are transient `apps/web` interface behavior;
- copying text invokes no shortage command and creates no shortage history, audit event, or notification;
- the popup displays only the user-facing value selected under decisions 10.374–10.380.

MVP:
- full displayed text can be selected;
- standard copy works where supported by the platform;
- the popup remains open while the user selects or copies its text.
