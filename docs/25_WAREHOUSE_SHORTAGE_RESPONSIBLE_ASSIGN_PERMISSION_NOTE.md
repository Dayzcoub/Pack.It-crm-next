# 25 Warehouse — Shortage Responsible Assign Permission Note

## 10.273. Who can assign or change responsible person for shortage

Decision: responsible person for a shortage can be assigned or changed by the warehouse keeper, admin, and director.

Rules:
- assigned warehouse keeper can assign or change responsible person;
- admin can assign or change responsible person;
- director can assign or change responsible person;
- assignment is done only from the shortage detail card;
- assignment/change action is logged in the shortage action history;
- the open shortage list shows current responsible person or unassigned state.

Purpose:
- keep shortage ownership manageable by warehouse role;
- allow admin/director override when needed;
- preserve accountability for assignment changes.

MVP approach:
- permissions: warehouse keeper, admin, director;
- no inline assignment from list row;
- detail card contains assignment control and writes action to history.
