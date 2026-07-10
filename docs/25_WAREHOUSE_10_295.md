# 25 Warehouse 10.295

Decision: if an assigned user's proposal is accepted only in part, treat it as acceptance with adjustment rather than as an unrelated separate action.

Example:
- assigned user proposes `found: 3`;
- warehouse keeper confirms `found: 2`;
- the proposal is recorded as accepted with adjustment;
- only the confirmed quantity affects the shortage balance.

MVP:
- partial acceptance is linked to the original proposal;
- history shows both the proposed and confirmed values;
- assigned user receives the same acceptance notification, with the adjustment visible;
- the remaining shortage stays open if the confirmed quantity does not cover it fully;
- the final action is performed by warehouse keeper, admin, or director and is logged normally.
