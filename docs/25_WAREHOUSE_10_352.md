# 25 Shortages 10.352

Decision: project and section context in the message about a shortage that is no longer visible are shown in one line with explicit labels.

Behavior:
- the message identifies the shortage according to the previously defined naming rules;
- project and section are rendered on one line;
- both values keep explicit labels, for example: `Проект: Концерт | Раздел: Свет`;
- if a value is absent, the corresponding label remains and the value is shown as `Не указан`;
- the formatting remains readable for keyboard and assistive-technology users and does not rely only on punctuation or visual styling to distinguish the fields.

Architecture binding:
- the displayed project and section values come from the current read projection available to `apps/web`;
- this presentation rule does not change the shortage domain state or the underlying project/section references;
- rendering or removing the message creates no shortage history, audit event, side effect, or notification.

MVP:
- project and section appear in one line;
- both use explicit labels;
- missing values use `Не указан`;
- the message remains informational and contains no action button.
