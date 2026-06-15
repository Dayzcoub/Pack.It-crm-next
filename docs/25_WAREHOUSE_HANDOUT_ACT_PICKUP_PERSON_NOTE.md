# 25 Warehouse — Handout Act Pickup Person Note

## 10.160. Physical pickup person in the handout act

Decision: the handout act should record who physically picked up the equipment from the warehouse.

Rules:
- record the warehouse user who handed out the equipment;
- record the person who physically picked up the equipment;
- the pickup person may be a driver, technician, project manager, contractor, or another assigned person;
- the pickup person can be different from the project manager;
- the pickup person should be shown in the handout act.

Purpose:
- make responsibility clear at the moment equipment leaves the warehouse;
- support real workflows where a driver or technician collects equipment for the project;
- avoid ambiguity between project ownership and physical pickup.

MVP approach:
- add a pickup person field to the handout act;
- allow selecting from project team / company users where possible;
- allow a text value for external pickup person if needed later;
- store date and time through system confirmation.
