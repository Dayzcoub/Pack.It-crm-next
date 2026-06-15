# 25 Warehouse — Problem Report Permission Note

## 10.196. Who can create an internal problem/loss report

Decision: any user with access to inventory operations and warehouse changes can create an internal warehouse problem/loss report.

Rules:
- do not limit report creation only to manager or admin roles;
- allow users with inventory access and warehouse change permission to create the report;
- the report is created manually from one or more problem rows;
- the action should still be logged with user, date, time, and source problem rows.

Purpose:
- let warehouse and technical staff document problems when they discover them;
- avoid blocking real warehouse workflow on manager/admin availability;
- keep accountability through permissions and audit logs.

MVP approach:
- allow report creation for roles/users that can perform inventory and warehouse changes;
- store created-by metadata;
- keep the report internal by default.
