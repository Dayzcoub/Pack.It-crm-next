# 25 Shortages 10.351

Decision: project and section context in the message about a shortage that is no longer visible is displayed with explicit field labels.

Behavior:
- the message includes the shortage name or position according to the established identification rules;
- project context is shown as `Проект: <значение>`;
- section context is shown as `Раздел: <значение>`;
- the two attributes are visually distinguishable and are not merged into an unlabeled compact string;
- when either value is absent, the corresponding field remains visible with `Не указан` according to decision 10.350.

Architecture binding:
- the displayed values come from the current read projection available to `apps/web` after conflict reconciliation;
- labels and formatting are presentation concerns and do not modify the shortage aggregate or source data;
- rendering the message invokes no `shortages` command and creates no shortage history, audit event, side effect, or notification.

MVP:
- use the explicit labels `Проект:` and `Раздел:`;
- always render both fields in the same order;
- use `Не указан` for a missing value;
- keep the message informational without filter-reset or other action controls.
