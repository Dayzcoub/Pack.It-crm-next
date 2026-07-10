# 25 Warehouse 10.290

Decision: proposed shortage result is shown only in the action history, not as a separate top block in the detail card.

MVP:
- do not add a separate "responsible proposal" block at the top;
- add proposal as a normal action history event;
- history event stores actor, time, selected result, quantity or reason where applicable;
- notification still points to the shortage detail card.
