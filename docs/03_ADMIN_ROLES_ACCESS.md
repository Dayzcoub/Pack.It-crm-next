# 03. Системная админка, роли и доступы

## 1. Главное разделение

В PACK.IT нужно разделить три разных уровня управления:

```text
1. Системная админка приложения
2. Проектная работа
3. Складская работа
```

Эти уровни связаны, но не должны смешиваться.

## 2. Системная админка приложения

Системная админка отвечает за само приложение, а не за конкретный склад или конкретную смету.

Системный администратор управляет:

- пользователями;
- ролями;
- правами доступа;
- ключами и приглашениями;
- настройками компании;
- логотипами;
- PDF-шаблонами;
- фирменным стилем документов;
- системными справочниками;
- доступными модулями;
- аудитом действий;
- глобальными настройками приложения.

## 3. Что системный админ НЕ должен делать по умолчанию

Системный администратор не обязательно должен быть менеджером проекта или складским пользователем.

Админка приложения не должна автоматически означать:

- участие в проектах;
- редактирование всех смет;
- складские операции;
- выдачу оборудования;
- списание оборудования;
- подтверждение резервов;
- изменение коммерческих условий проекта.

Эти права должны выдаваться явно.

## 4. Проектные роли

Проектные роли работают с проектами и сметами.

Предварительный список:

- Owner / владелец пространства;
- Director / руководитель;
- Project Manager / менеджер проекта;
- Technical Director / технический директор;
- Technician / техник;
- Sound Engineer;
- Light Engineer;
- LED Engineer;
- Stage / Truss Technician;
- Driver;
- Invited Specialist;
- Viewer.

## 5. Складские роли

Складские роли работают с оборудованием и движениями.

Предварительный список:

- Inventory Admin;
- Warehouse Manager;
- Warehouse Operator;
- Equipment Editor;
- Reservation Manager;
- Readonly Warehouse Viewer.

## 6. Системные роли

Системные роли управляют самой программой.

Предварительный список:

- App Owner;
- System Admin;
- Access Manager;
- PDF Template Manager;
- Branding Manager;
- Directory Manager;
- Audit Viewer.

## 7. Принцип прав доступа

Роли не должны быть жёстко зашиты только как названия.

Нужна модель:

```text
Role
→ Permissions
→ Module Access
→ Action Access
→ Scope
```

Пример:

```text
role: Project Manager
permissions:
  - project.view
  - project.create
  - project.edit_commercial
  - project.export_client_pdf
  - client.view
  - client.edit
  - inventory.check_availability
```

## 8. Типы прав

### 8.1. Project permissions

- project.view;
- project.create;
- project.edit;
- project.edit_commercial;
- project.edit_technical;
- project.change_status;
- project.approve;
- project.archive;
- project.delete;
- project.view_internal_costs.

### 8.2. Scene permissions

- scene.view;
- scene.create;
- scene.edit;
- scene.delete;
- scene.export_images;
- scene.generate_bom.

### 8.3. Inventory permissions

- inventory.view;
- inventory.edit_items;
- inventory.check_availability;
- inventory.reserve;
- inventory.release_reserve;
- inventory.issue;
- inventory.return;
- inventory.move;
- inventory.writeoff;
- inventory.view_costs.

### 8.4. Documents permissions

- documents.view;
- documents.generate_client_pdf;
- documents.generate_internal_pdf;
- documents.edit_templates;
- documents.edit_branding;
- documents.send_to_client.

### 8.5. Admin permissions

- admin.users.view;
- admin.users.create;
- admin.users.disable;
- admin.roles.edit;
- admin.keys.issue;
- admin.branding.edit;
- admin.pdf_templates.edit;
- admin.directories.edit;
- admin.audit.view;
- admin.modules.configure.

## 9. Ключи и приглашения

Система должна поддерживать ключи доступа:

- постоянные;
- временные;
- проектные;
- для приглашённых специалистов;
- с ограничением по датам;
- с ограничением по роли;
- с ограничением по проекту;
- с возможностью отзыва.

## 10. Приглашённый специалист

Приглашённый специалист может иметь ограниченный доступ только к конкретному проекту.

Например:

- видеть дату и адрес;
- видеть свою роль;
- видеть техническое задание;
- видеть нужные документы;
- оставить комментарий;
- подтвердить участие.

Он не должен видеть:

- все проекты;
- склад целиком;
- внутреннюю маржу;
- чужие ставки;
- системную админку;
- настройки компании.

## 11. PDF и брендирование

Настройки PDF и брендирования должны быть в системной админке.

Администратор должен иметь возможность настроить:

- логотип компании;
- название компании;
- реквизиты;
- контактные данные;
- цветовую тему документа;
- видимость блоков;
- шаблон коммерческого предложения;
- шаблон технической сводки;
- шаблон складского листа;
- подписи и футеры.

## 12. Аудит

Важные действия должны попадать в журнал:

- вход пользователя;
- создание проекта;
- изменение проекта;
- изменение суммы;
- изменение прав;
- выдача ключа;
- изменение PDF-шаблона;
- складской резерв;
- выдача оборудования;
- возврат оборудования;
- изменение системных настроек.

## 13. Главный принцип

Админка приложения должна быть самостоятельным модулем.

Нельзя смешивать системную админку, складскую админку и проектную работу в один экран только потому, что у пользователя есть высокий уровень доступа.
