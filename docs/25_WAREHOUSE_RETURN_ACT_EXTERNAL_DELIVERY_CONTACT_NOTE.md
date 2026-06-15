# 25 Warehouse — Return Act External Delivery Contact Note

## 10.172. External delivery contact fields in the return act

Decision: if equipment is returned by an external person, the return act should use the same contact fields as the handout act.

Rules:
- name or organization is required for an external delivery person;
- phone should be available as a field;
- comment should be available as a field;
- this data is stored in the internal warehouse return record and return act;
- entering an external delivery person does not create a system user.

Purpose:
- make it clear who physically brought equipment back;
- keep a contact phone if the team needs to clarify return details;
- allow notes such as car number, company name, route, or return context.

MVP approach:
- add external delivery name field;
- add external delivery phone field;
- add external delivery comment field;
- show these fields in the internal return act when filled.
