# Проект Taski‑Docker

<a name="Start-point"></a>
* [О проекте](#About)<br/>
* [Как запустить проект](#How-to-run)<br/>
* [Документация на API](#Examples)<br/>

<a name="About"></a>
## О проекте

### Описание проекта

Сервис Taski‑Docker предназначен для управления задачами и списками дел с использованием Docker‑контейнеризации. Проект позволяет:
* создавать, редактировать и удалять задачи;
* отмечать задачи как выполненные;
* просматривать списки задач с фильтрацией по статусу;
* работать с проектом в изолированной Docker‑среде.

#### Авторы учебного проекта:
Команда ЯндексПрактикума

#### Выполнил учебный проект:
Водолейкин Виталий, студент факультета python backend developer <br/>
когорты 116 - 121 (2025 - 2026 гг.]) <br/>
([GitHub](https://github.com/VitalyVodoleikin), [Telegram](https://t.me/vodoleikin_v))

### Технические подробности

Стек технологий:
* Python
* Django
* PostgreSQL
* Docker
* Docker Compose
* Nginx
* Gunicorn
* Redis
* Celery
* и др. <br/>

<br>
<div style="display: flex; justify-content: space-between; align-items: center; width: 100%;">
  <img src="https://github.com/devicons/devicon/blob/master/icons/python/python-original-wordmark.svg?raw=true" alt="Python" width="80" height="80"/>    
  <img src="https://github.com/devicons/devicon/blob/master/icons/django/django-plain.svg?raw=true" alt="Django" width="80" height="80"/>    
  <img src="https://github.com/devicons/devicon/blob/master/icons/postgresql/postgresql-original.svg?raw=true" alt="PostgreSQL" width="80" height="80"/>    
  <img src="https://github.com/devicons/devicon/blob/master/icons/docker/docker-original.svg?raw=true" alt="Docker" width="80" height="80"/>    
  <img src="https://github.com/devicons/devicon/blob/master/icons/nginx/nginx-original.svg?raw=true" alt="Nginx" width="80" height="80"/>
  <img src="https://github.com/devicons/devicon/blob/master/icons/redis/redis-original.svg?raw=true" alt="Redis" width="80" height="80"/>
</div>
<br>

Проект развёртывается в контейнеризированной среде с помощью Docker и Docker Compose. Используются отдельные контейнеры для:
* веб‑приложения (Django + Gunicorn);
* базы данных (PostgreSQL);
* веб‑сервера (Nginx);
* фоновых задач (Celery + Redis).

<a name="How-to-run"></a>
## Как запустить проект Taski‑Docker:

1. Клонировать репозиторий и перейти в него в командной строке:
```
git clone 
cd taski-docker
```

2. Убедиться, что установлены Docker и Docker Compose:
* Для Linux/macOS: следуйте официальной инструкции по установке Docker Engine и Docker Compose.
* Для Windows: установите Docker Desktop.

3. Создать файл `.env` в корневой директории проекта с переменными окружения (подставьте свои значения):
```
SECRET_KEY=your_django_secret_key
DEBUG=0

POSTGRES_DB=taski
POSTGRES_USER=taski_user
POSTGRES_PASSWORD=your_secure_password

DB_HOST=db
DB_PORT=5432
```

4. Запустить контейнеры с помощью Docker Compose:
```
docker-compose up -d
```
Это запустит все сервисы в фоновом режиме.

5. Выполнить миграции базы данных:
```
docker-compose exec web python manage.py migrate
```

6. Создать суперпользователя для доступа к админ‑панели Django:
```
docker-compose exec web python manage.py createsuperuser
```
Следуйте инструкциям в терминале для ввода имени пользователя и пароля.

7. Собрать статические файлы (если требуется):
```
docker-compose exec web python manage.py collectstatic --noinput
```

8. (Опционально) Заполнить базу данных тестовыми данными:
```
docker-compose exec web python manage.py loaddata sample_data.json
```

<a name="Examples"></a>
## Документация на API

После запуска проекта документация API будет доступна по адресам:
* [http://127.0.0.1:8000/api/docs/](http://127.0.0.1:8000/api/docs/) — интерактивная документация Swagger/OpenAPI;
* [http://127.0.0.1:8000/api/](http://127.0.0.1:8000/api/) — корневой URL API.

Админ‑панель Django доступна по адресу:
[http://127.0.0.1:8000/admin/](http://127.0.0.1:8000/admin/)

<p align="right"><a href="#Start-point">Вернуться к началу</a></p>
