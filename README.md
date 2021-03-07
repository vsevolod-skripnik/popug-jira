Фёдор, Антон, я не успел доделать до конца, но начал делить на акторов и команды


# Вторая домашка

## 1. Разобрать каждое требование на составляющие (актор, команда и событие). Определить, какие акторы будут в системе и какие события нужны. 

### Таск-трекер

1. Таск-трекер должен быть отдельным дашбордом и доступен всем сотрудникам компании UberPopug Inc.

```
Actor: любой сотрудник
Command: считать дашборд тасков
Data: таски
Event: дашборд тасков считан
```

2. Авторизация в таск-трекере должна выполняться через общий сервис авторизации UberPopug Inc (у нас там инновационная система авторизации на основе формы клюва).

```
Actor: любой сотрудник
Command: авторизоваться
Data: сотрудник, данные для входа
Event: сотрудник авторизован
```

3. В таск-трекере должны быть только задачи. Проектов, скоупов и спринтов никому не надо, ибо минимализм.

```
Actor: —
Command: — 
Data: задача
Event: —
```

4. В таск-трекере новые таски может создавать кто угодно. У задачи должны быть описание, статус (выполнена или нет) и попуг, на которого заассайнена задача.

```
Actor: любой сотрудник
Command: создать задачу
Data: сотрудник, задача (описание, статус, исполнитель)
Event: задача создана
```

5. Менеджеры или администраторы должны иметь кнопку «заассайнить задачи», которая возьмет все открытые задачи и рандомно заассайнит каждую на любого из сотрудников. Не успел закрыть задачу до реассайна — сорян, делай следующую.

```
Actor: сотрудник с ролью менеджера или админа
Command: заассайнить все задачи
Data: открытые задачи, исполнители
Event: задачи заассайнены
```

6. Каждый сотрудник должен иметь возможность видеть в отдельном месте список заассайненных на него задач + отметить задачу выполненной.

```
Actor: сотрудник
Command: считать свои задачи
Data: сотрудник, его задачи
Event: сотрудник считал задачи

Actor: сотрудник
Command: закрыть задачу
Data: сотрудник, задача
Event: сотрудник закрыл задачу
```

7. После ассайна новой задачи сотруднику должно приходить оповещение на почту, в слак и в смс.

```
Actor: событие «Сотрудник получил задачу»
Command: отправить оповещения
Data: сотрудник, задача
Event: три события — отправить уведомление на почту, в слак и смс
```

### Аккаунтинг: кто сколько денег заработал

1. Аккаунтинг должен быть в отдельном дашборде и доступным только для администраторов и бухгалтеров.

```
Actor: сотрудник с ролью админа или бухгалтера
Command: прочитать дашборд аккаунтинга
Data: некие данные аккаунтинга, счёт к примеру
Event: дашборд аккаунтинга считан
```

2. Авторизация в таск-трекере должна выполняться через общий сервис авторизации UberPopug Inc.

`Это повтор из пункта про таск-трекер`

3. У каждого из сотрудников должен быть свой счет, который показывает, сколько за сегодня он получил денег. У счета должен быть аудитлог того, за что были списаны или начислены деньги, с подробным описанием каждой из задач.

```
Actor: —
Command: — 
Data: счёт сотрудника
Event: —

Actor: —
Command: — 
Data: аудитлог счёта сотрудника
Event: —
```

4. Расценки:у сотрудника появилась новая задача — `rand(-10..-20)$`, сотрудник выполнил задачу — `rand(20..40)$`

```
Actor: событие «Сотрудник получил задачу»
Command: списать деньги из счёта компании
Data: счёт компании, счёт сотрудника, сотрудник
Event: сотруднику на счёт переведены деньги

Actor: событие «Сотрудник закрыл задачу»
Command: начилить счёту компании деньги
Data: сотрудник, счёт компании
Event: на счёт компании начислены деньги
```

5. Вверху выводить количество заработанных за сегодня денег.

```
Actor: —
Command: —
Data: количество заработанных за сегодня денег ← нужно хранить и обновлять задачами из пункта 4
Event: — 
```

6. В конце дня необходимо считать, сколько денег сотрудник получил за рабочий день, слать на почту сумму выплаты.

7. После выплаты баланса (в конце дня) он должен обнуляться и в аудитлоге должно быть отображено, что была выплачена сумма.

8. Дашборд должен выводить информацию по дням, а не за весь период сразу.


### Аналитика

1. Аналитика — это отдельный дашборд, доступный только админам.
2. Нужно указывать, сколько заработал топ-менеджмент: сколько программистов ушло в минус.
3. Нужно показывать самую дорогую задачу за: день, неделю и месяц.


## 2. Построить модель данных и модель доменов. Рисовать можно хоть на листочке, главное, чтобы это было не только у вас в голове, но и где-то вовне.

## 3. Определиться, какие общие данные нужны для разных доменов и как связаны данные между разными доменами.
