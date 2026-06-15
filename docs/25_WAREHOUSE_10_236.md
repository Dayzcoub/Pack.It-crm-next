# Warehouse 10.236

Decision: repeated scan of the same item in the current handout or return scan list should only show a message. The item is not added again.

Rules:
- check current scan list before adding;
- if item is already present, show message;
- keep one row for the item;
- continue scanning.
