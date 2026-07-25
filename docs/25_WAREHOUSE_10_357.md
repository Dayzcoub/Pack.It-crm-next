# 25 Shortages 10.357

Decision: when the available width is insufficient for a convenient one-line display of both the project and section, the context switches to a two-line layout.

Behavior:
- the project and section are no longer forced into the same line when this would make both values difficult to read;
- the first line shows `Проект: …`;
- the second line shows `Раздел: …`;
- each value may use the full available width of its own line;
- the one-line separator `|` is not shown in the two-line layout;
- the existing missing-value representation `Не указан` remains unchanged;
- if a value is still too long for its full line, the truncation and full-text disclosure rules from decision 10.354 continue to apply.

Architecture binding:
- choosing the one-line or two-line representation is responsive `apps/web` presentation logic;
- the layout decision does not change the shortage, project, or section data contracts;
- it invokes no `shortages` command and creates no shortage history, audit event, side effect, or notification.

MVP:
- use one line while both labelled values remain conveniently readable;
- switch to two lines when the available width is insufficient;
- preserve the explicit `Проект:` and `Раздел:` labels in both layouts;
- retain keyboard and assistive-technology access to the full value when visual truncation is required.
