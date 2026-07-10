# PACK.IT Communication and Field Operations Skill

Use this skill before implementing chats, notifications, task assignments, crew workflows, checklists, onsite communication, intercom roadmap, project events, or field execution states.

## Main rule

Communication is not a side chat. In PACK.IT, communication must be tied to projects, tasks, roles, responsibility, field status and audit where needed.

## Communication layers

```text
Project communication
  -> project chat / threads / comments / mentions
  -> object/zone/task comments
  -> client-visible comments where allowed

Operational notifications
  -> assignments
  -> status changes
  -> shortages
  -> approvals
  -> deadlines
  -> warehouse discrepancies
  -> site issues

Field workflows
  -> tasks
  -> checklists
  -> loading / return confirmations
  -> photo reports
  -> issue escalation
  -> responsible person handoff

Future field comms / intercom
  -> integration or controlled bridge to external realtime voice systems
```

## Task model principles

A task should have:

- project;
- title/description;
- role/category;
- assignee/responsible person;
- due date or project phase;
- status;
- priority;
- related section/object/warehouse line where relevant;
- comments/history;
- attachments/photos where relevant.

Tasks can be generated from project state, not only manually created.

Examples:

- warehouse pick list creates scan tasks;
- deficit creates responsible assignment;
- tech pack approval creates review task;
- return discrepancy creates issue task;
- client comment creates manager/tech response task.

## Notifications

Notifications should be actionable and scoped:

- who needs this;
- why now;
- what action is expected;
- where it leads;
- what happens if ignored.

Do not spam everyone. Prefer role/project/responsibility targeting.

## Field communication / intercom roadmap

Treat intercom/voice as a future field-comms layer. Do not build it into core project logic too early.

Possible future approaches:

- integration with external voice systems;
- WebRTC/LiveKit-style project rooms;
- Telegram/Discord bridge for early MVP;
- role/zone channels;
- push-to-talk style mobile workflow;
- project radio/channel reference stored in project data.

MVP should focus first on project chats, notifications, tasks, checklists and mobile field workflow. Voice/intercom can be designed as an integration layer later.

## Permissions

- Internal project chat is not visible to client by default.
- Client-visible comments must be explicitly separated.
- Technicians should see operational data needed for execution, not full commercial/internal financial data unless permitted.
- Warehouse sees warehouse-relevant data and project context needed for loading/return.
- All privileged or critical changes should be auditable.

## Red flags

- Generic global chat unrelated to project/task context.
- Notifications without clear next action.
- Client comments mixed with internal crew discussion.
- Field checklist results not persisted in project history.
- Intercom built as core dependency before basic task/chat workflows exist.
