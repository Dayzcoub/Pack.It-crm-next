# 25 Warehouse — Shortage List Unassigned State Note

## 10.270. Unassigned responsible state in shortage list

Decision: if a shortage does not have an assigned responsible person yet, the open shortage list should show a compact unassigned state.

Rules:
- do not hide the responsible field when no one is assigned;
- show compact text: unassigned;
- the state must be visually restrained and must not clutter the row;
- once responsible person is assigned, replace unassigned state with the assigned person;
- full assignment details and history remain inside the shortage detail card.

Purpose:
- make it clear which shortages still need assignment;
- avoid ambiguity caused by an empty field;
- keep the warehouse keeper list actionable.

MVP approach:
- shortage row includes responsible field;
- if responsible is null, show compact label: unassigned;
- opening detail card allows assignment/change according to permissions.
