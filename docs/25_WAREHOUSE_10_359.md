# 25 Shortages 10.359

Decision: after the project and section context switches to a two-line layout, each value remains limited to one visual line and is shortened with an ellipsis when necessary.

Behavior:
- the project and section are displayed on separate lines according to decision 10.357;
- each line keeps its explicit label: `Проект: …` and `Раздел: …`;
- each value is independently constrained to one visual line;
- overflowing values are shortened with an ellipsis;
- the full value remains available on pointer hover and keyboard focus according to decision 10.354;
- the placeholder `Не указан` from decision 10.350 is not shortened unless the container is narrower than the minimum supported layout.

Architecture binding:
- the displayed values come from the shortage read projection or the last confirmed client projection used during conflict reconciliation;
- truncation and two-line layout are presentation concerns owned by `apps/web`;
- the UI does not alter or persist shortened values;
- displaying, focusing, or revealing the full text invokes no shortage command and creates no shortage history, audit event, notification, or other domain side effect.

MVP:
- two separate context lines are used when the container cannot keep both values readable in one line;
- each value remains single-line and may be truncated with an ellipsis;
- full values are accessible by hover and keyboard focus;
- internal technical identifiers are not exposed.
