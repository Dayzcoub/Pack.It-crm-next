# 25 Warehouse 10.300

Decision: if the warehouse keeper, admin, or director keeps the same result type but changes its reason or explanation, treat the action as acceptance of the assigned user's proposal with adjustment.

Examples:
- assigned user proposes `write off` with reason `damaged during loading`;
- warehouse keeper confirms `write off` with reason `damaged during operation`;
- the proposal is accepted with adjustment;
- assigned user proposes `accounting error` with one explanation;
- the final confirmer keeps `accounting error` but replaces the explanation;
- the proposal is accepted with adjustment.

MVP:
- keeping the same result type allows acceptance with adjustment;
- changed reason or explanation is stored as the corrected final value;
- the confirmer must provide a mandatory reason explaining why the proposal was changed;
- history shows the original proposal, the corrected reason or explanation, and the adjustment reason;
- the assigned user receives an acceptance-with-adjustment notification containing the corrected result and the adjustment reason.
