# 25 Warehouse — Handout Act External Pickup Person Note

## 10.161. External pickup person in the handout act

Decision: if equipment is picked up by an external driver or contractor, the handout act should allow entering that person manually.

Rules:
- the pickup person may be selected from company/project users when available;
- if the person is not in the team, the user may enter the pickup person manually;
- this manual entry is used only for the act and warehouse record;
- manual entry does not automatically create a user account;
- the handout act should still record who handed out the equipment and when.

Examples:
- external driver;
- subcontractor;
- courier;
- temporary helper.

Purpose:
- support real warehouse handout workflows;
- avoid forcing every external pickup person into the user database;
- keep responsibility visible in the internal document.

MVP approach:
- add pickup person text field for external pickup;
- optionally keep phone/comment for later, but not mandatory for MVP;
- show the manually entered pickup person in the internal handout act.
