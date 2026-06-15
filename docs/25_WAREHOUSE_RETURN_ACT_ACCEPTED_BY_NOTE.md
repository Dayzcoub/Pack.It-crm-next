# 25 Warehouse — Return Act Accepted By Note

## 10.173. Accepted by user in the return act

Decision: the return act should record who accepted the equipment at the warehouse.

Rules:
- record the person who physically delivered the equipment back;
- record the user who accepted the return at the warehouse;
- this user may be a warehouse worker, technician, project manager, or another user with proper access;
- the accepted-by user should be shown in the internal return act;
- date and time are stored through system confirmation.

Purpose:
- make responsibility clear at the return point;
- support small teams without a dedicated warehouse worker;
- keep a reliable internal record of who accepted the equipment.

MVP approach:
- add accepted-by field to the return act;
- fill it from the authenticated user who confirms the return where possible;
- allow users with proper permissions to perform the return confirmation;
- keep the return act internal.
