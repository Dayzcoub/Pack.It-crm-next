# 25 Warehouse — Transfer Simple Status Note

## 10.147. Simple transfer statuses

Decision: project-to-project transfer needs only two operational status marks for MVP: departed and delivered.

Rules:
- do not add a complex logistics workflow at MVP stage;
- the transfer block starts as planned;
- when the equipment leaves the first site, mark it as departed;
- when the equipment reaches the second site, mark it as delivered;
- additional mandatory stages are not needed at the start.

Statuses:
- planned;
- departed;
- delivered.

Data to store:
- who marked departed;
- departed timestamp;
- who marked delivered;
- delivered timestamp;
- optional comment.

Purpose:
- the first project can see that the equipment has left;
- the second project can see that the equipment is on the way or already delivered;
- the process stays simple for technicians and warehouse users.

MVP approach:
- show these statuses in the transfer block of both related picking lists;
- allow the responsible user or a permitted project/warehouse user to update the transfer status;
- keep advanced logistics stages for later if needed.
