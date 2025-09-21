Базовые:
1. **Запустить контейнер Ubuntu** и выполнить в нём `ls` (через `docker run` с `it`).
2. **Запустить nginx** и открыть его в браузере (`docker run -d -p 8080:80 nginx`).
3. **Посмотреть список контейнеров** (`docker ps`, `docker ps -a`) и остановить/удалить один.
4. **Посмотреть список образов** (`docker images`).
5. **Удалить ненужный контейнер и образ** (`docker rm`, `docker rmi`).


Работа с Dockerfile:
1. Создать простой `Dockerfile` с Python и `app.py` (печатает "Hello from Docker").
    - Собрать образ (`docker build -t my-python-app .`).
    - Запустить контейнер.
2. Изменить `app.py` (например, другое сообщение) и пересобрать образ.
    - Показать разницу между старым и новым образом.
3. Загрузить образ в DockerHub:
    - Переименовать образ (`docker tag my-python-app <username>/my-python-app:v1`).
    - Залогиниться (`docker login`).
    - Запушить (`docker push <username>/my-python-app:v1`).


Сделать `Dockerfile` на базе `nginx`, который копирует свой `index.html`.

- `index.html` → "Docker works, nginx works, Hi ITC".
- Собрать образ.
- Запустить контейнер и открыть страницу в браузере.
