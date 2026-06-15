# 25 Warehouse — Problem Report Manual Creation Note

## 10.191. Internal problem/loss report creation

Decision: the internal warehouse problem/loss report should be created manually by button from a problem row.

Rules:
- do not automatically create a formal report for every problem row;
- allow creating the report manually when the team decides it is needed;
- the source should be a return problem row, inventory discrepancy, or another warehouse problem record;
- the report is internal by default.

Purpose:
- avoid unnecessary paperwork;
- keep lightweight problem rows for normal warehouse workflow;
- create a formal internal report only for meaningful cases.

MVP approach:
- add a Create problem report button on eligible problem rows;
- prefill the report from the source problem data;
- allow the user to review/edit before saving;
- keep generated reports in internal document history where applicable.
