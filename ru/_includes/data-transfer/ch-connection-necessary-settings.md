{% list tabs %}

* MDB кластер

    Подключение к БД с указанием идентификатора кластера в {{ yandex-cloud }}. Доступно только для кластеров, развернутых в сервисе {{ mch-name }}.

    Для подключения задайте обязательные параметры:

    * **Идентификатор кластера MDB**, к которому необходимо подключиться.
    * **Имя базы данных** в кластере.
    * **Имя пользователя** базы данных, от имени которого сервис {{ data-transfer-name }} будет подключаться к базе.
    * **Пароль** пользователя для доступа к базе данных.

* OnPremise кластер

    Подключение к БД с явным указанием сетевых адресов хостов и портов.

    Для подключения задайте обязательные параметры:

    * **Шарды**.

        Для каждого шарда укажите:

        * идентификатор;
        * FQDN или IP-адреса хостов.

    * **Подключение через SSL**.
    * **PEM-сертификат**, если требуется шифрование передаваемых данных, например для соответствия требованиям [PCI DSS](https://storage.yandexcloud.net/yc-compliance/certificates/YC_PCI_DSS_Guide.pdf). Загрузите файл [сертификата](../../managed-clickhouse/operations/connect#get-ssl-cert) или добавьте его содержимое в текстовом виде.
    * **HTTP порт**.

        При подключении через HTTP-порт:

        * Для необязательных полей будут использованы значения по умолчанию, если они заданы.
        * Поддерживается запись сложных типов (`array`, `tuple` и т. д.).

    * **Нативный порт**.
    * **Имя базы данных** в кластере.
    * **Имя пользователя** базы данных, от имени которого сервис {{ data-transfer-name }} будет подключаться к базе.
    * **Пароль** пользователя для доступа к базе данных.

{% endlist %}