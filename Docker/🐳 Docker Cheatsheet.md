# 🐳 Docker Практика — Чек-лист

---

## 1. Запуск контейнеров

- Запустить Ubuntu:
    
    ```bash
    docker run -it ubuntu
    
    ```
    
- Внутри контейнера выполнить:
    
    ```bash
    ls
    exit
    
    ```
    
- Запустить nginx и пробросить порт:
    
    ```bash
    docker run -d -p 8080:80 nginx
    
    ```
    
- Проверить в браузере → [http://localhost:8080](http://localhost:8080/)

---

## 2. Управление контейнерами и образами

- Посмотреть контейнеры:
    
    ```bash
    docker ps
    docker ps -a
    
    ```
    
- Остановить контейнер:
    
    ```bash
    docker stop <container_id>
    
    ```
    
- Удалить контейнер:
    
    ```bash
    docker rm <container_id>
    
    ```
    
- Посмотреть образы:
    
    ```bash
    docker images
    
    ```
    
- Удалить образ:
    
    ```bash
    docker rmi <image_id>
    
    ```
    

---

## 3. Dockerfile (Python)

Создать `app.py`:

```python
print("Hello from Docker!")

```

Создать `Dockerfile`:

```docker
FROM python:3.9-slim
WORKDIR /app
COPY app.py .
CMD ["python", "app.py"]

```

Собрать образ:

```bash
docker build -t my-python-app .

```

Запустить:

```bash
docker run my-python-app

```

---

## 4. DockerHub

- Залогиниться:
    
    ```bash
    docker login
    
    ```
    
- Тегнуть образ:
    
    ```bash
    docker tag my-python-app <dockerhub_username>/my-python-app:v1
    
    ```
    
- Запушить:
    
    ```bash
    docker push <dockerhub_username>/my-python-app:v1
    
    ```
    

---

## 5. Мини-проект с Nginx

Создать `index.html`:

```html
<!DOCTYPE html>
<html>
  <body>
    <h1>Docker works</h1>
    <h1>Nginx works</h1>
    <p>Hi ITC 🚀</p>
  </body>
</html>

```

Создать `Dockerfile`:

```docker
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html

```

Собрать образ:

```bash
docker build -t my-nginx .

```

Запустить контейнер:

```bash
docker run -d -p 8080:80 my-nginx

```

Проверить → [http://localhost:8080](http://localhost:8080/)

---