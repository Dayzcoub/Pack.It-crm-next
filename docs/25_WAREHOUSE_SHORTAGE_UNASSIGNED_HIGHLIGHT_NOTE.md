# 25 Warehouse — Shortage Unassigned Highlight Note

## 10.271. Highlight unassigned shortages

Decision: if a shortage has no assigned responsible person, the row should be highlighted as requiring assignment.

Rules:
- row still shows compact text: unassigned;
- unassigned row gets subtle visual highlight;
- highlight must not clutter or overload the interface;
- highlight should indicate that assignment is needed;
- after responsible person is assigned, highlight is removed;
- full assignment action and history remain inside the shortage detail card.

Purpose:
- make unassigned shortages noticeable in the warehouse keeper list;
- help warehouse keeper quickly find items requiring delegation;
- keep daily workflow clean but actionable.

MVP approach:
- add compact unassigned label;
- apply restrained highlight style to unassigned rows;
- remove highlight automatically once responsible person is assigned.
