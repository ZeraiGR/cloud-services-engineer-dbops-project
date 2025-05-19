# dbops-project
Исходный репозиторий для выполнения проекта дисциплины "DBOps"

## Используемые SQL команды (шаг 3, создание нового пользователя и выдача ему необходимых прав на базу данных store):

```
CREATE DATABASE store;
\l -- Проверка того, что таблица создана
CREATE USER store_user WITH PASSWORD 'secure_password’;
GRANT ALL PRIVILEGES ON DATABASE store TO store_user;
\c store -- Переключение на БД store
GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO store_user;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT ALL PRIVILEGES ON TABLES TO store_user;
GRANT ALL PRIVILEGES ON ALL SEQUENCES IN SCHEMA public TO store_user;
ALTER DEFAULT PRIVILEGES IN SCHEMA public
GRANT ALL PRIVILEGES ON SEQUENCES TO store_user;
```

## Используемая SQL команда для шага 10, выборки данных из нескольких таблиц

SELECT o.date_created, SUM(op.quantity)
FROM orders AS o
JOIN order_product AS op ON o.id = op.order_id
WHERE o.status = 'shipped' AND o.date_created > NOW() - INTERVAL '7 DAY'
GROUP BY o.date_created;

## Используемые SQL команды для шага 11, создания индексов

CREATE INDEX order_product_order_id_idx ON order_product(order_id);
CREATE INDEX orders_status_date_idx ON orders(status, date_created);
