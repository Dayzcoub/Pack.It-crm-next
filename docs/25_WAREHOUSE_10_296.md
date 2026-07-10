# 25 Warehouse 10.296

Decision: when a warehouse keeper, admin, or director accepts an assigned user's proposal with an adjustment, they must provide a reason for the change.

Example:
- assigned user proposes `found: 3`;
- warehouse keeper confirms `found: 2`;
- the action is treated as acceptance with adjustment;
- the person confirming the result must explain why the confirmed value differs from the proposal.

MVP:
- the adjustment reason is required before the action can be saved;
- the reason is stored together with the final action;
- history shows the original proposal, the confirmed result, and the adjustment reason;
- the assigned user receives an acceptance notification with the corrected result;
- the remaining shortage stays open if the confirmed quantity does not cover it fully.
