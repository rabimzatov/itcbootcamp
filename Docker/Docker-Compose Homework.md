## 🏠 Домашнее задание: Docker Compose

**Задача:**
Развернуть простое приложение «WordPress + MySQL» с помощью `docker-compose.yml`.

**Требования:**

1. Создать файл `docker-compose.yml`, в котором:

   * сервис `db`: образ `mysql:5.7`, пароль root → `rootpass`, отдельный volume для данных;
   * сервис `wordpress`: образ `wordpress:latest`, проброс порта 8080 → 80, переменные окружения для подключения к базе (`WORDPRESS_DB_HOST=db`, `WORDPRESS_DB_USER=root`, `WORDPRESS_DB_PASSWORD=rootpass`).
2. Запустить проект командой:

   ```bash
   docker-compose up -d
   ```
3. Проверить, что WordPress доступен по адресу `http://localhost:8080`.
4. Остановить проект командой:

   ```bash
   docker-compose down
   ```
5. Убедиться, что данные MySQL сохранились в volume (т.е. при повторном запуске база не «с нуля»).

**Дополнительно (для желающих):**

* Подключить phpMyAdmin (образ `phpmyadmin`) как третий сервис, пробросив порт `8081:80`.
* Настроить его так, чтобы он подключался к тому же MySQL (`PMA_HOST=db`).