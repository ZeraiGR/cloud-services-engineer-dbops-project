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

