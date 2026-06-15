# 25 Warehouse — Problem Cause at Detection Note

## 10.195. When the problem cause is filled

Decision: the problem cause is filled when the problem is detected, not only during report creation.

Rules:
- the problem/discrepancy row should contain the cause field from the moment the issue is detected and recorded;
- the internal problem/loss report should pull this cause from the source problem row;
- report generation should not force the user to invent the cause again;
- the cause can still be reviewed or clarified when creating the report if permissions allow it.

Purpose:
- capture context while the situation is fresh;
- avoid losing important details before a formal report is created;
- make report creation faster and more accurate.

MVP approach:
- add cause input to the problem row workflow;
- prefill report cause fields from source rows;
- keep the report internal by default.
