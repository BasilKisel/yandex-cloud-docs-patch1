# pg_cron

Расширение [pg_cron](https://github.com/citusdata/pg_cron) — это планировщик задач, который позволяет добавлять в базу данных задачи по расписанию и выполнять SQL-запросы прямо из задачи.

## Установить расширение pg_cron в кластер {{ PG }} {#pg_cron-install}

Чтобы установить расширение `pg_cron` в кластер {{ PG }}:

1. [Подключите к кластеру библиотеку общего пользования](./cluster-extensions.md#libraries-connection) с именем `pg_cron`.
1. [Добавьте расширение](./cluster-extensions.md#update-extensions) `pg_cron` к одной из баз данных. Подключить расширение к двум базам данных нельзя.

    {% note warning %}

    Установка расширения `pg_cron` приведет к последовательной перезагрузке {{ PG }} на всех хостах кластера.

    {% endnote %}

1. [Добавьте пользователю](../grant.md#grant-privilege), который будет управлять задачами, [роль `mdb_admin`](../../concepts/roles.md#mdb-admin).

В выбранной базе данных появится схема `cron` с таблицами и функциями, необходимыми для работы расширения:

* Таблицы:

    * `cron.job` — содержит запланированные задачи. Разрешена команда `SELECT`.
    * `cron.job_run_details` — содержит историю запусков расширения. Разрешены команды `SELECT`, `UPDATE`, `DELETE`.

* Функции:

    * `schedule` — создает задачу в базе данных, в которой установлено расширение `pg_cron`.
    * `schedule_in_database` — создает задачу в другой базе данных.
    * `unschedule` — удаляет задачу.
    * `alter_job` — изменяет задачу.

Подробнее о расширении `pg_cron` см. в [официальной документации](https://github.com/citusdata/pg_cron).

{% note warning %}

Функция `schedule_in_database` позволяет создать задачу в другой базе данных, даже если у пользователя нет необходимого разрешения. Таким образом, установка расширения `pg_cron` позволит пользователю с ролью `mdb_admin` обходить ограничения прав доступа.

{% endnote %}
