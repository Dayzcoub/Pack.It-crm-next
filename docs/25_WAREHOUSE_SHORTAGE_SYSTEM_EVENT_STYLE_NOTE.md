# 25 Warehouse — Shortage System Event Style Note

## 10.266. Visual style for system events in shortage history

Decision: system events in shortage action history should be visually separated from human actions.

Rules:
- system events use a separate neutral/gray visual style;
- system events may include a system icon/label;
- user actions keep normal user/action styling;
- system events and user actions are still shown in one chronological timeline;
- visual separation should make it clear what was automatic and what was done by a person.

Purpose:
- avoid confusing automatic system changes with user actions;
- keep the action history readable;
- make audit review easier.

MVP approach:
- add event type badge: user/system;
- show system events with gray styling and system label/icon;
- keep timestamp and changed result visible.
