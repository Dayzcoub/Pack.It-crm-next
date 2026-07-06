# 25 Warehouse — Shortage Responsible Any Company User Note

## 10.274. Any company user can be assigned as shortage responsible

Decision: any company user can be assigned as the responsible person for a shortage, not only users with warehouse or technical roles.

Rules:
- warehouse keeper, admin, and director can assign responsible person from the shortage detail card;
- candidate list may include any active company user;
- assigned responsible person is shown in the open shortage list row;
- if no one is assigned, row shows unassigned state and subtle highlight;
- assignment/change is logged in the shortage action history.

Purpose:
- allow assigning investigation to the person who actually has context;
- support cases where manager, driver, technician, or another employee knows what happened;
- avoid artificial restriction by role.

MVP approach:
- responsible picker searches/selects from all active company users;
- no role filter for warehouse/technical users only;
- keep permissions for assigning/changing limited to warehouse keeper, admin, and director.
