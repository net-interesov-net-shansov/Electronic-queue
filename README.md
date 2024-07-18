# Электонная очередь

Система электронной очереди с выдачей талонов и базой данных принятых клиентов, написана в формате сайта.
Есть возможность редактировать количество администраторов и группировать талоны по цели прибытия, а также выводить саму очереди на экраны любых размеров.

![Logotype](./static/Logo.svg)
## Использумые технологии и их документации
- Написано на - [Python версии 3.7 или выше](https://docs.python.org/3/index.html).
- Фреймворк - [Flask](https://flask.palletsprojects.com/en/3.0.x/).
- Динамическая обработка данных и двунаправленная связь сервер-клиент - [flask-socketio](https://flask-socketio.readthedocs.io/en/latest/).
- База данных - [flask_sqlalchemy](https://flask-sqlalchemy.palletsprojects.com/en/3.1.x/).

## Структура и иерархия сайта
**Функционал страниц:**<br>
 - [add.html](/templates/add.html)<br>
 Добавление строк в таблицы базы данных.
 - [admin.html](/templates/admin.html)<br>
 Просмотр содержимого базы данных, перенаправление на add.html.
 - [base.html](/templates/base.html)<br>
 Базовый шаблон для всех страниц, подключение jquery, навбар.
 - [index.html](/templates/index.html)<br>
 Главная страница, перенаправление на monitor.html, admin.html, login.html.
 - [login.html](/templates/login.html)<br>
 Стриница входа для персонала, перенапраение на manager.html и operator.html.
 - [manager.html](/templates/monitor.html)<br>
 Страница менеджера, вживую принимающего клиентов,
 интерфейс страницы рассчитан на использование с мобильных уст-в или планшетов.
 - [monitor.html](/templates/monitor.html)<br>
 Демонстрация электронной очереди для клиентов. При вызове талона оператором, звучит короткий звуковой сигнал и очередь обновляется в реальном времени.
 Вёрстка страницы рассчитана на большие 2к экраны.
 - [operator.html](/templates/operator.html)<br>
 Позволяет оператору приглашать клиентов к окну/кабинету.
 - [table.html](/templates/table.html)<br>
 Вывод таблиц в панели admin.html

**Cерверная часть**:
 - [queue.db](/instance/)<br>
 Хранит всех клиентов, прошедших через эл. очередь,<br>
 все возможные операции, для выбора клиентом,<br>
 всех операторов и привязанные к ним операции.
 - [app.py](/app.py)<br>
 Исполняемый файл. Запуск сервера, взаимодействие с базой данных, адресация.

**Скрипты**:
 - [manager.js](/static/manager.js)<br>
 Отправка данных клиента в базу данных.
 - [monitorScripts.js](/static/monitorScripts.js)<br>
 Вывод приглашённых приглашённых клиентов на экран.
 - [operator.js](/static/operator.js)<br>
 Вывод очереди ожидания оператору. Возможность просмотра информации и приглашения клиента.
 - [timeProcessing.js](/static/timeProcessing.js)<br>
 Вывод реального времени в base.html.