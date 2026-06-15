# 25 Warehouse — In Repair Destination Note

## 10.213. Repair destination tracking

Decision: when an item receives in_repair status, the system must record where it was sent for repair.

Repair destination options:
- internal repair;
- external contractor;
- service center.

Rules:
- in_repair status should not be just a bare status without destination context;
- record repair destination type;
- record organization/person/contact details where applicable;
- record who sent the item to repair and when;
- record comments such as repair reason, expected return date, or repair notes where applicable;
- in_repair remains unavailable for booking/reservation.

Purpose:
- keep damaged/non-working equipment traceable;
- avoid losing items while they are outside the warehouse;
- support repair follow-up and operational accountability.

MVP approach:
- require repair destination type when moving item to in_repair;
- allow optional repair contact/comment fields;
- log the status transition with user, date, time, and source problem/report if available.
