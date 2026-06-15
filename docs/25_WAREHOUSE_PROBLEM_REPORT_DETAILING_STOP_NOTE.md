# 25 Warehouse — Problem Report Detailing Stop Note

## 10.203. Stop detailing the internal problem/loss report

Decision: the internal warehouse problem/loss report has enough detail for the current warehouse documentation stage.

Already fixed:
- report creation is manual, from problem rows;
- several related problems can be combined into one report;
- photos and files are shown as small previews where possible;
- the probable cause is recorded when the problem is detected and pulled into the report;
- users with access to inventory operations and warehouse changes can create the report;
- reports are stored in warehouse document history;
- default MVP retention guideline is the last 6 months;
- the report includes a resolution/action field;
- the report can be created before a final resolution is known;
- unresolved reports use requires resolution status;
- who can close requires resolution is configurable by company admin/director;
- closing a resolution can automatically update the warehouse item status;
- before applying an automatic status change, the user must confirm the consequence.

Decision on PDF/print detailing:
- do not add more detail now;
- current report structure is enough for MVP documentation;
- PDF/print layout can reuse general warehouse document patterns later.

Next documentation area:
- move to summarizing warehouse document rules or the next warehouse workflow block.
