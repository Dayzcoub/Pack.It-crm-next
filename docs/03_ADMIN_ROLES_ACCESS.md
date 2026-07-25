# 03. Системная админка, роли и доступы

## 1. Главное разделение

В PACK.IT нужно разделить три разных уровня управления:

```text
1. Системная админка приложения
2. Проектная работа
3. Складской контур
```

Эти уровни связаны, но не должны смешиваться.

Складской контур в интерфейсе может быть единым разделом, но permissions внутри него разделяются по контекстам `catalog`, `inventory`, `reservations`, `shortages`, `subrent` и `warehouse-operations`.

## 2. Системная админка приложения

Системная админка отвечает за само приложение, а не за конкретный склад или конкретную смету.

Системный администратор управляет:

- пользователями;
- ролями;
- permissions;
- scope доступа;
- ключами и приглашениями;
- настройками компании;
- логотипами;
- PDF-шаблонами;
- фирменным стилем документов;
- системными справочниками;
- доступными модулями;
- системным audit log;
- глобальными настройками приложения.

## 3. Что системный админ НЕ должен делать по умолчанию

Системный администратор не обязательно является менеджером проекта или складским пользователем.

Админка приложения не должна автоматически означать:

- участие в проектах;
- редактирование всех смет;
- изменение складских остатков;
- подтверждение резервов;
- принятие предложения по нехватке;
- финальное закрытие нехватки;
- выдачу оборудования;
- возврат оборудования;
- списание оборудования;
- подтверждение субаренды;
- изменение коммерческих условий проекта.

Эти permissions выдаются явно.

Даже `App Owner` и `System Admin` проходят обычную application authorization. Название роли не является обходом доменных правил.

## 4. Принцип модели доступа

PACK.IT использует модель:

```text
Role
→ Permissions
→ Module Access
→ Action Access
→ Scope
```

Роль является удобным набором permissions, а не жёстко зашитым списком исключений.

Проверка доступа выполняется application use case владельца действия.

Например:

```text
role: Warehouse Manager
permissions:
  - inventory.view
  - reservations.confirm
  - shortages.assign
  - shortages.accept_proposal
  - shortages.resolve
  - warehouse_operations.issue
  - warehouse_operations.return
scope:
  - organization
  - selected warehouses
```

## 5. Проектные роли

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

Наличие роли `Director` или `Technical Director` не предоставляет `shortages.resolve`, `inventory.correct_balance` или `warehouse_operations.writeoff` автоматически.

## 6. Складские роли

Предварительные role presets:

- Inventory Admin;
- Warehouse Manager;
- Warehouse Operator;
- Equipment Editor;
- Reservation Manager;
- Shortage Resolver;
- Subrent Manager;
- Readonly Warehouse Viewer.

Каждый preset собирается из permissions и может быть ограничен scope конкретной организации, склада, проекта или локации.

## 7. Системные роли

Предварительный список:

- App Owner;
- System Admin;
- Access Manager;
- PDF Template Manager;
- Branding Manager;
- Directory Manager;
- Audit Viewer.

Системные роли управляют программой и доступами, но не получают продуктовые permissions автоматически.

## 8. Типы permissions

### 8.1. Project permissions

```text
project.view
project.create
project.edit
project.edit_commercial
project.edit_technical
project.change_status
project.approve
project.archive
project.delete
project.view_internal_costs
project.request_fulfillment_check
```

### 8.2. Scene permissions

```text
scene.view
scene.create
scene.edit
scene.delete
scene.export_images
scene.generate_bom
```

### 8.3. Catalog permissions

```text
catalog.view
catalog.edit
```

### 8.4. Inventory permissions

```text
inventory.view
inventory.edit_items
inventory.correct_balance
inventory.view_costs
```

`inventory.correct_balance` предназначен для учётной корректировки. Он не закрывает нехватку напрямую.

### 8.5. Reservation permissions

```text
reservations.view
reservations.create
reservations.confirm
reservations.release
```

### 8.6. Shortage permissions

```text
shortages.view
shortages.assign
shortages.propose_resolution
shortages.accept_proposal
shortages.resolve
```

Разделение действий:

- `shortages.propose_resolution` позволяет назначенному ответственному предложить результат;
- `shortages.accept_proposal` позволяет принять предложение или принять его с допустимой корректировкой;
- `shortages.resolve` позволяет выполнить отдельное финальное решение;
- эти permissions не предоставляются через системную роль автоматически.

### 8.7. Subrent permissions

```text
subrent.view
subrent.create
subrent.confirm
subrent.cancel
subrent.view_costs
```

### 8.8. Warehouse operation permissions

```text
warehouse_operations.view
warehouse_operations.issue
warehouse_operations.return
warehouse_operations.move
warehouse_operations.writeoff
```

Списание выполняется `warehouse-operations`, даже если его инициирует разрешение нехватки в `shortages`.

### 8.9. Documents permissions

```text
documents.view
documents.generate_client_pdf
documents.generate_internal_pdf
documents.edit_templates
documents.edit_branding
documents.send_to_client
```

### 8.10. Admin permissions

```text
admin.users.view
admin.users.create
admin.users.disable
admin.roles.edit
admin.keys.issue
admin.branding.edit
admin.pdf_templates.edit
admin.directories.edit
admin.audit.view
admin.modules.configure
```

`admin.*` не заменяет permissions продуктовых контекстов.

## 9. Scope доступа

Permission всегда может быть ограничен scope:

- всей системой;
- организацией;
- workspace;
- конкретным проектом;
- складом;
- локацией;
- назначенной пользователю нехваткой;
- ограниченным периодом времени.

Пример:

```text
permission: shortages.propose_resolution
scope:
  shortageId: shortage-123
  assignedUserId: current-user
```

## 10. Ключи и приглашения

Система должна поддерживать ключи доступа:

- постоянные;
- временные;
- проектные;
- для приглашённых специалистов;
- с ограничением по датам;
- с ограничением по роли;
- с ограничением по permissions;
- с ограничением по проекту или другой сущности;
- с возможностью отзыва.

## 11. Приглашённый специалист

Приглашённый специалист может иметь ограниченный доступ только к конкретному проекту или назначенному действию.

Например:

- видеть дату и адрес;
- видеть свою роль;
- видеть техническое задание;
- видеть нужные документы;
- оставить комментарий;
- подтвердить участие;
- предложить результат по назначенной нехватке при наличии `shortages.propose_resolution`.

Он не должен видеть:

- все проекты;
- склад целиком;
- чужие нехватки;
- внутреннюю маржу;
- чужие ставки;
- системную админку;
- настройки компании.

## 12. PDF и брендирование

Настройки PDF и брендирования находятся в системной админке.

Администратор с соответствующими permissions может настроить:

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

## 13. История и аудит

Нужно различать:

- доменную историю проекта;
- доменную историю резерва;
- доменную историю нехватки;
- историю субаренды;
- историю складских операций;
- системный audit log.

Audit log фиксирует значимые действия:

- вход пользователя;
- создание проекта;
- изменение проекта;
- изменение суммы;
- изменение permissions;
- выдачу или отзыв ключа;
- изменение PDF-шаблона;
- создание и подтверждение резерва;
- предложение и финальное разрешение нехватки;
- учётную корректировку;
- выдачу, возврат, перемещение и списание;
- изменение системных настроек.

Audit log не является единственным источником текущего состояния и не подменяет доменную историю владельца данных.

## 14. Authorization для предложений по нехватке

Термины `warehouse keeper`, `admin` или `director` в ранних decision notes не являются самостоятельными правилами доступа.

Каноническая трактовка:

```text
предложить результат
→ shortages.propose_resolution

принять предложение
→ shortages.accept_proposal

выполнить другой финальный результат
→ shortages.resolve
```

Если финальное решение требует учётной или физической складской операции, дополнительно проверяется permission владельца этой операции, например:

```text
inventory.correct_balance
warehouse_operations.writeoff
```

## 15. Главный принцип

Системная админка, проектная работа и складской контур остаются отдельными поверхностями продукта.

Нельзя смешивать их в один набор неограниченных прав только потому, что пользователь имеет высокую должность или системную роль.

Каждое критическое действие должно иметь:

- конкретный permission;
- понятный scope;
- application authorization;
- проверку текущего состояния;
- доменную историю;
- системный audit при необходимости.