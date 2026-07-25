# 25 Shortages 10.350

Decision: when the project or section value is absent, the disappearance message keeps both context fields and shows `Не указан` for the missing value.

Behavior:
- the message identifies the shortage by its visible item name;
- the context always contains both fields: project and section;
- when a field has no value, its value is rendered as `Не указан`;
- the available field keeps its actual displayed value;
- the same structure is used whether one field or both fields are missing;
- the message remains under the shortages-list heading until the list is refreshed or the filters are changed, according to the established message lifecycle.

Architecture binding:
- project and section values come from the current server-backed read projection available to `apps/web`;
- `Не указан` is a presentation fallback and is not written back as domain data;
- rendering the fallback does not modify the shortage, project, section, filter state, audit history, or notifications;
- no `shortages.*` command is invoked by showing or clearing the message.

MVP:
- always render both labels: project and section;
- use the exact fallback text `Не указан` for each absent value;
- do not hide an absent field or replace it with an empty string;
- keep the message informational and without a filter-reset action.
