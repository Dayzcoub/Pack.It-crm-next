# 25 Shortages 10.325

Decision: when the form moves through remaining validation errors, it follows the visual order of fields from top to bottom.

Behavior:
- the next error is the first invalid field located below the field that was just corrected;
- if no invalid field remains below, the flow continues from the first invalid field at the top of the form;
- the system does not reorder errors by validation type or business priority;
- required-field, format, and other validation errors participate in the same visual sequence;
- automatic focus and scrolling follow the rules defined in 10.323 and 10.324.

MVP:
- error navigation is predictable and matches the visual structure of the form;
- users are not moved unexpectedly between distant fields because of hidden error priorities;
- the first invalid field on save is selected using the same top-to-bottom order;
- all entered form data remains preserved while navigating through errors;
- server-side validation remains authoritative before the shortages action is committed.