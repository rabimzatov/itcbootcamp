
## ✅ Задание по **Docker Network**

**Цель:** понять, как работает пользовательская сеть и DNS между контейнерами.

**Задание:**

1. Создайте сеть `testnet`:

   ```bash
   docker network create testnet
   ```
2. Запустите два контейнера в этой сети:

   ```bash
   docker run -dit --name web --network testnet ubuntu
   docker run -dit --name db -e MYSQL_ROOT_PASSWORD=root --network testnet mysql
   ```
3. Зайдите внутрь контейнера `web`:

   ```bash
   docker exec -it web bash
   ```

4. Установите ping, так как по умолчанию в простых образах он не установлен:
   ```bash
   apt-get update && apt-get install -y iputils-ping dnsutils
   ```
5. Проверьте доступность `db` по имени:

   ```bash
   ping db
   ```

**Ожидаемый результат:**

* Контейнер `web` может пинговать контейнер `db` по имени, без использования IP.
* При подключении к другой сети этого бы не было.

---

## ✅ Задание по **Docker-Compose**

**Цель:** познакомиться с базовым использованием `docker-compose.yml`.

**Задание:**

1. Создайте файл `docker-compose.yml` с двумя сервисами:

   * `web`: Nginx, проброс порта 8080 → 80.
   * `db`: MySQL, пароль `root`.

   ```bash
   version: "3.9"
   services:
     web:
       image: nginx
       ports:
         - "8080:80"
     db:
       image: mysql
       environment:
         MYSQL_ROOT_PASSWORD: root
   ```
2. Запустите оба контейнера одной командой:

   ```bash
   docker-compose up -d
   ```
3. Проверьте список сервисов:

   ```bash
   docker-compose ps
   ```
4. Откройте в браузере `http://localhost:8080` → должен открыться стартовый экран Nginx.
5. Остановите и удалите окружение:

   ```bash
   docker-compose down
   ```

**Ожидаемый результат:**

* Сервисы запущены одной командой.
* В браузере открывается Nginx.
* MySQL контейнер поднят, доступен по имени `db`.

---