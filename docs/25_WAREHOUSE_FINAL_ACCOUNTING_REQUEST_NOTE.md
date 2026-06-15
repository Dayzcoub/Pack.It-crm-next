# 25 Warehouse — Final Accounting Request Note

## 10.219. Request and approval flow for final accounting action

Decision: warehouse users can create a request for the final accounting action with an explanation, but only admin/director can confirm the final action.

Rules:
- warehouse user can send a request with a required explanation/comment;
- the request does not perform the final action automatically;
- admin/director reviews the request and confirms or rejects it;
- confirmation by admin/director performs the final status/action;
- request, review, confirmation/rejection, user, date, time, and comments must be logged.

Purpose:
- let warehouse users initiate the process when the issue is detected;
- keep final accounting authority with admin/director;
- preserve accountability and audit trail.

MVP approach:
- add request flow for final accounting action;
- require explanation from requester;
- require admin/director confirmation for final completion.
