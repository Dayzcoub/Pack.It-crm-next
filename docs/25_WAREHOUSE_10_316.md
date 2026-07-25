# 25 Shortages 10.316

Decision: when a user has edited text that was automatically transferred into a mandatory reason or explanation field, switching to a result without that field requires confirmation before the edited text is discarded.

Behavior:
- if the transferred text still exactly matches the original proposal comment, switching results follows the normal automatic-clear rule without an extra warning;
- if the user has made any meaningful edit, the system asks for confirmation before removing the text;
- the warning explains that the unsaved edited explanation will be lost;
- confirming switches the result type and clears the transferred text;
- cancelling keeps the current result type and preserves the edited text;
- no data is written to `shortages` until the separate resolution action is submitted successfully.

MVP:
- the warning appears only when edited unsaved transferred text exists;
- the confirmation provides clear continue and cancel actions;
- continue discards the edited text and opens the result without a mandatory explanation field;
- cancel preserves the current form state;
- the original proposal and its comment remain unchanged in shortage history;
- final resolution still requires `shortages.resolve` and normal server-side validation.
