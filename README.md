# Проект taski-docker
## Проект предназначен для отработки практических навыков разворачивания приложений в docker контейнерах

## Сборка образов

Сборка образов на архитектуре x86_64
```
docker build -t densad/taski_backend backend/
docker build -t densad/taski_frontend frontend/
docker build -t densad/taski_gateway gateway/
```


Сборка образов на MACOS c чипом Apple Silicon
```
cd backend
docker buildx build --platform=linux/amd64 -t densad/taski_backend .
cd ../frontend
docker buildx build --platform=linux/amd64 -t densad/taski_frontend .
cd ../gateway
docker buildx build --platform=linux/amd64 -t densad/taski_gateway .
```

Загрузка созданных образов в docker hub
```
docker push densad/taski_backend
docker push densad/taski_frontend
docker push densad/taski_gateway 
```

## Запуск приложения в Docker контейнерах

В коренвом каталоге проекта создать файл окружения:

```
nano .env
```

пример содержимого файла окружения 

```
POSTGRES_DB='django'
POSTGRES_USER='django'
POSTGRES_PASSWORD='password'
DB_HOST='db'
PORT=5432
```

Выполнить сборку и запуск необходимых контейнеров

```
docker compose up -d
```