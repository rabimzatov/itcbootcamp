# 📝 Задание 1. Python + Dockerfile

## app.py

(готовый код, менять не нужно)

```python
print("Hello from my first Docker image!")
```

## Dockerfile (каркас)

```dockerfile
FROM python:3.10-slim

# ??? (нужно выбрать директорию работы)

# ??? (нужно скопировать app.py внутрь контейнера)

# ??? (нужно указать команду запуска python app.py)
```

---

# 📝 Задание 2. Docker Compose (Web + DB)

## docker-compose.yml (каркас)

```yaml
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
```


---

# 📝 Задание 3. Docker Hub

1. Собрать образ (но тег с пропуском):

   ```bash
   docker build -t ??? .
   ```

2. Запушить:

   ```bash
   docker push ???
   ```

---

# 📝 Задание 4. Docker Network

## Задание

1. Создать сеть:

   ```bash
   docker network create testnet
   ```

2. Запустить контейнеры:

   ```bash
   docker run -dit --name web --network testnet nginx
   docker run -dit --name db --network testnet ???:5.7
   ```

3. Проверить внутри контейнера `web`:

   ```bash
   docker exec -it web bash
   # установить утилиту и проверить доступность db
   apt-get update && apt-get install -y iputils-ping
   ping db
   ```

---


Хочешь, я оформлю это как **единый “лист заданий для студентов” в PDF**, чтобы ты мог им сразу раздать?
