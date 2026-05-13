# Kittygram 🐱

Kittygram — это веб-приложение для публикации информации о котиках.
Пользователи могут добавлять своих питомцев, загружать фотографии, указывать достижения котиков и просматривать карточки других питомцев.

Проект развёрнут в Docker-контейнерах и полностью автоматизирован с помощью CI/CD на GitHub Actions.

---

# Возможности проекта

* Регистрация и авторизация пользователей
* Добавление котиков
* Загрузка изображений питомцев
* Указание цвета, даты рождения и достижений
* Административная панель Django Admin
* REST API
* React frontend
* Автоматическая сборка Docker-образов
* Автоматическое тестирование проекта
* Отправка уведомлений в Telegram после успешного workflow

---

# Технологии

## Backend

* Python 3.9
* Django
* Django REST Framework
* Gunicorn

## Frontend

* React
* JavaScript
* Node.js

## Database

* PostgreSQL 13

## Infrastructure

* Docker
* Docker Compose
* Nginx

## CI/CD

* GitHub Actions
* Docker Hub
* Telegram Bot API

---

# Структура проекта

```text
kittygram_final/
├── backend/                # Django backend
├── frontend/               # React frontend
├── nginx/                  # Конфигурация Nginx
├── docker-compose.yml
└── .github/workflows/      # GitHub Actions
```

---

# Как развернуть проект локально

## 1. Клонировать репозиторий

```bash
git clone https://github.com/YOUR_USERNAME/kittygram_final.git
cd kittygram_final
```

---

# 2. Создать .env файл

В корне проекта создайте файл `.env`.

Пример содержимого:

```env
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password

DB_NAME=kittygram
DB_HOST=db
DB_PORT=5432

SECRET_KEY=super_secret_key

ALLOWED_HOSTS=localhost,127.0.0.1
```

---

# 3. Запустить контейнеры

```bash
docker compose up --build
```

---

# 4. Выполнить миграции

В новом терминале:

```bash
docker compose exec backend python manage.py migrate
```

---

# 5. Собрать статические файлы

```bash
docker compose exec backend python manage.py collectstatic
```

---

# 6. Создать суперпользователя

```bash
docker compose exec backend python manage.py createsuperuser
```

---

# 7. Открыть проект

## Главная страница

```text
http://localhost:9000
```

## Django Admin

```text
http://localhost:9000/admin
```

---

# Docker контейнеры

Проект использует следующие контейнеры:

| Контейнер | Назначение     |
| --------- | -------------- |
| gateway   | Nginx          |
| backend   | Django backend |
| frontend  | React frontend |
| db        | PostgreSQL     |

---

# Docker volumes

| Volume  | Назначение              |
| ------- | ----------------------- |
| pg_data | Данные PostgreSQL       |
| static  | Статические файлы       |
| media   | Загружаемые изображения |

---

# CI/CD

Проект использует GitHub Actions.

Workflow автоматически:

* запускает тесты backend и frontend;
* проверяет backend через Ruff;
* собирает Docker-образы;
* отправляет образы на Docker Hub;
* отправляет уведомление в Telegram.

---

# Docker Hub

Образы проекта:

* `YOUR_DOCKER_USERNAME/kittygram_backend`
* `YOUR_DOCKER_USERNAME/kittygram_frontend`
* `YOUR_DOCKER_USERNAME/kittygram_gateway`

---

# GitHub Actions Secrets

Для работы CI/CD необходимо добавить Secrets в GitHub:

| Secret          | Описание                           |
| --------------- | ---------------------------------- |
| DOCKER_USERNAME | Логин Docker Hub                   |
| DOCKER_PASSWORD | Пароль или Access Token Docker Hub |
| TELEGRAM_TOKEN  | Токен Telegram бота                |
| TELEGRAM_TO     | Telegram chat id                   |

---

# Автор

Проект выполнен в рамках учебного проекта Yandex Practicum.
