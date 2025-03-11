# ddl-dml

Задание 1
1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.

1.2. Создайте учётную запись sys_temp.

1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)

![1](https://github.com/AlexandeAbel/ddl-dml/blob/main/img/1.jpg)

1.4. Дайте все права для пользователя sys_temp.

1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (В скриншоте выше.)

1.6. Переподключитесь к базе данных от имени sys_temp.

Для смены типа аутентификации с sha2 используйте запрос:

ALTER USER 'sys_test'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
1.6. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.

1.7. Восстановите дамп в базу данных.

1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)

![1](https://github.com/AlexandeAbel/ddl-dml/blob/main/img/2.jpg)

Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.

1.2
CREATE USER 'sys_temp'@'localhost' 
IDENTIFIED WITH mysql_native_password 
BY '';

1.3
SELECT * FROM mysql.user \G

1.4
GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'localhost';

1.5
SHOW GRANTS FOR 'sys_temp'@'localhost' \G

1.6
mysql -u sys_temp -p

wget https://downloads.mysql.com/docs/sakila-db.zip

1.7 
unzip ...
CREATE DATABASE sakila;
mysql -u sys_temp -p sakila < sakila-schema.sql
mysql -u sys_temp -p sakila < sakila-data.sql

1.8
USE sakila;
SHOW TABLES;

Задание 2.
Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст)

Название таблицы | Название первичного ключа
customer         | customer_id

Acter - actor_id;
Acter_info - actor_id;
Address - address_id;
Category - category_id;
City - city_id,country_id;
Country - country_id;
Customer - customer_id, store_id;
Customer_list - ID;
Film - film_id,language_id,original_language_id;
Film_actor - actor_id, film_id;
Film_category - film_id, category_id;
Film-list - FID;
Film-text - film_id;
Inventory - inventory_id, film_id, store_id;
Language - language_id;
nicer_but_slower_film_list - FID;
payment - payment_id, customer_id, staff_id, rental_id;
Rental - retnal_id, inventory_id, customer_id, staff_id;
Staff - staff_id;
Staff_list - ID
Store - store_id,manager_staff_id, address_id