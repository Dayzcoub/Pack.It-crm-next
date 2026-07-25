# 25 Shortages 10.375

Decision: the full-text window opened from a truncated context value shows only the value the user selected.

Behavior:
- selecting the truncated project value opens the full project name;
- selecting the truncated section value opens the full section name;
- the second context value is not duplicated in the window;
- the window title or field label identifies whether the displayed value is the project or the section;
- the source list remains unchanged behind the window;
- the window is informational and does not allow editing.

Architecture binding:
- the displayed value comes from the existing shortage read projection or the last confirmed client projection;
- opening and closing the window is transient `apps/web` state;
- the interaction invokes no shortage command and creates no shortage history, audit event, or notification;
- decision 10.374 remains the governing simplification for touch interaction.

MVP:
- a tap on a truncated project opens only the project value;
- a tap on a truncated section opens only the section value;
- no unrelated context is duplicated;
- the value is shown in full and read-only.
