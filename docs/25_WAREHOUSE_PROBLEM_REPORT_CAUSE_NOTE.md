# 25 Warehouse — Problem Report Cause Note

## 10.194. Problem/loss report probable cause

Decision: the internal warehouse problem/loss report should include a probable cause field.

Rules:
- allow the user to specify the probable cause of the problem;
- the cause is not always final proof, it can be a working assumption;
- the cause should be editable before saving the report;
- if multiple problems are combined into one report, each problem row can have its own cause where needed.

Example causes:
- lost on site;
- damaged during transport;
- returned incomplete;
- picking error;
- warehouse accounting error;
- wrong storage place;
- client/site-related issue;
- unknown / requires review.

Purpose:
- help the team understand not only what happened, but why it may have happened;
- support later analysis of recurring warehouse problems;
- help separate damage, loss, accounting errors, and process mistakes.

MVP approach:
- add a probable cause field to the internal problem/loss report;
- support a predefined list plus optional free comment where practical;
- keep the report internal by default.
