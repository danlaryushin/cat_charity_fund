![Python](https://img.shields.io/badge/-Python-222324?style=for-the-badge&logo=Python&logoColor=yellow)
![FastAPI](https://img.shields.io/badge/-FastAPI-222324?style=for-the-badge&logo=FastAPI)
![SQLAlchemy](https://img.shields.io/badge/-SQLAlchemy-222324?style=for-the-badge&logo=SQLAlchemy)
![Alembic](https://img.shields.io/badge/-Alembic-222324?style=for-the-badge&logo=Alembic)
![Pydantic](https://img.shields.io/badge/-Pydantic-222324?style=for-the-badge&logo=Pydantic&logoColor=FF1493)
![Asyncio](https://img.shields.io/badge/-Asyncio-222324?style=for-the-badge&logo=Asyncio)

# Приложение QRKot


![alt text](https://pictures.s3.yandex.net/resources/sprint2_picture1_1672399951.png)

## Описание

Учебный проект для изучения работы во фреймворке FastAPI.

**QRkot** - это API сервиса по сбору средств для финансирования благотворительных проектов. В сервисе реализована возможность регистрации пользователей, добавления благотворительных проектов и пожертвований, которые распределяются по открытым проектам.

Настроено автоматическое создание первого суперпользователя при запуске проекта.

## Установка
1. Склонируйте репозиторий:
```
git clone git@github.com:Hastred45/cat_charity_fund.git
```
2. Активируйте venv и установите зависимости:
```
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```
3. Создайте в корневой директории файл .env со следующим наполнением:
```
APP_TITLE=Приложение QRKot.
APP_DESC=Спасем котиков вместе!
DATABASE_URL=sqlite+aiosqlite:///./<название базы данных>.db
SECRET=<секретное слово>
FIRST_SUPERUSER_EMAIL=<email суперюзера>
FIRST_SUPERUSER_PASSWORD=<пароль суперюзера>
```
4. Примените миграции для создания базы данных SQLite:
```
alembic upgrade head
```
5. Проект готов к запуску.

## Управление:
Для локального запуска выполните команду:
```
uvicorn app.main:app --reload
```
Сервис будет запущен и доступен по следующим адресам:
- http://127.0.0.1:8000 - API
- http://127.0.0.1:8000/docs - автоматически сгенерированная документация Swagger
- http://127.0.0.1:8000/redoc - автоматически сгенерированная документация ReDoc

После запуска доступны следующие эндпоинты:
- Регистрация и аутентификация:
    - **/auth/register** - регистрация пользователя
    - **/auth/jwt/login** - аутентификация пользователя (получение jwt-токена)
    - **/auth/jwt/logout** - выход (сброс jwt-токена)
- Пользователи:
    - **/users/me** - получение и изменение данных аутентифицированного пользователя
    - **/users/{id}** - получение и изменение данных пользователя по id
- Благотворительные проекты:
    - **/charity_project/** - получение списка проектов и создание нового
    - **/charity_project/{project_id}** - изменение и удаление существующего проекта
- Пожертвования:
    - **/donation/** - получение списка всех пожертвований и создание пожертвования
    - **/donation/my** - получение списка всех пожертвований аутентифицированного пользователя

Со схемами запросов и ответов можно ознакомиться в документации или в файле со спецификацией - openapi.json.

## Автор

[Даниил Ларюшин](https://github.com/danlaryushin)
