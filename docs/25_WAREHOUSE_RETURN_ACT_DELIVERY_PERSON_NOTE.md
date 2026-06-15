# 25 Warehouse — Return Act Delivery Person Note

## 10.171. Physical delivery person in the return act

Decision: the return act should record who physically brought the equipment back to the warehouse.

Rules:
- record the warehouse user who accepted the return;
- record the person who physically delivered the equipment back;
- the delivery person may be a driver, technician, project manager, contractor, or another assigned person;
- the delivery person can be different from the project manager;
- the delivery person should be shown in the internal return act.

Purpose:
- make responsibility clear at the moment equipment returns to the warehouse;
- support real workflows where a driver or technician brings equipment back;
- avoid ambiguity between project ownership and physical delivery.

MVP approach:
- add a delivery person field to the return act;
- allow selecting from project team / company users where possible;
- allow a text value for external delivery person if needed;
- store date and time through system confirmation.
