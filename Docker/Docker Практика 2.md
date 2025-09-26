📝 Задание 1. Python + Dockerfile
app.py

(готовый код, менять не нужно)

print("Hello from my first Docker image!")

Dockerfile (каркас)
FROM python:3.10-slim

# ??? (нужно выбрать директорию работы)
WORKDIR /app

# ??? (нужно скопировать app.py внутрь контейнера)

# ??? (нужно указать команду запуска python app.py)


👉 Студент должен вставить COPY и CMD.

📝 Задание 2. Docker Compose (Web + DB)
docker-compose.yml (каркас)
services:
  web:
    build: .
    ports:
      - "8080:5000"
    environment:
      DB_HOST: ???    # имя сервиса базы
  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: ???   # придумать пароль
