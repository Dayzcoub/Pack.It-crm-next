# 25 Warehouse — Handout Act External Pickup Contact Note

## 10.162. External pickup contact fields

Decision: if the pickup person is external, the handout act should allow entering name, phone, and comment.

Rules:
- name or organization is required for an external pickup person;
- phone should be available as a field;
- comment should be available as a field;
- this data is stored only in the internal warehouse handout record and act;
- entering an external pickup person does not create a system user.

Purpose:
- make it clear who physically picked up the equipment;
- keep a contact phone if the team needs to reach the driver or contractor;
- allow notes such as car number, company name, route, or pickup context.

MVP approach:
- add external pickup name field;
- add external pickup phone field;
- add external pickup comment field;
- show these fields in the internal handout act when filled.
