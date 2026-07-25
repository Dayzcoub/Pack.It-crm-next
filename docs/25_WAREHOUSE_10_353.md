# 25 Shortages 10.353

Decision: in the informational message about a shortage that is no longer visible in the current list, the project and section are separated by a vertical bar.

Display format:
- `Проект: … | Раздел: …`;
- both labels remain explicit;
- the order is fixed: project first, section second;
- missing values continue to use `Не указан` according to decision 10.350.

Behavior:
- the separator is presentation only and does not change filtering, shortage identity, or reconciliation logic;
- the message remains under the shortages-list heading according to decision 10.345;
- the displayed project and section identify the shortage that disappeared from the current list according to decisions 10.347–10.352.

Architecture binding:
- the formatted message is transient `apps/web` UI state derived from the authoritative shortage projection;
- the separator and labels are not persisted as shortage-domain data;
- showing or removing the message invokes no `shortages` command and creates no shortage history, audit event, side effect, or notification.

MVP:
- render the context in the form `Проект: <value> | Раздел: <value>`;
- use `Не указан` for a missing project or section;
- keep the message informational and non-interactive.
