# API YAMDB

## *Проект YaMDb*
Через API можно оставить отзыв и оценку на произведение из категорий: Книги, Фильмы, Музыка. Список категорий можно расширить.
Другие пользователи могут просматривать отзывы.

## Стэк технологий:
- Python
- Django
- Django Rest Framework
- PostgreSQL
- Nginx
- Gunicorn
- Docker
- Docker-compose

### Запуск проекта:
- Склонируйте репозитрий на свой компьютер
`$ git clone https://github.com/StAndUP-ru/infra_sp2.git `
- Создайте `.env` файл в директории `infra/`, в котором должны содержаться следующие переменные:
    >DJANGO_KEY='ваш secret_key django'
    >DB_ENGINE=django.db.backends.postgresql\
    >DB_NAME= # название БД\
    >POSTGRES_USER= # ваше имя пользователя\
    >POSTGRES_PASSWORD= # пароль для доступа к БД\
    >DB_HOST=db\
    >DB_PORT=5432\
- Из папки `infra/` соберите образ при помощи docker-compose
`$ docker-compose up -d`
Если потребуется пересобрать контейнеры:
`$ docker-compose up -d --build`
- Создайте файлы миграции
`$ docker-compose exec web python manage.py makemigrations`
- Примените миграции
`$ docker-compose exec web python manage.py migrate`
- Соберите статику
`$ docker-compose exec web python manage.py collectstatic --no-input`
- Для доступа к админке создайте суперюзера
`$ docker-compose exec web python manage.py createsuperuser`
- Чтобы загрузить в базу данные из Вашего дампа
`$ docker-compose exec web python manage.py loaddata fixtures.json`

### Работа с проектом:
- Чтобы создать дамп базы
`$ docker-compose exec web python manage.py dumpdata > fixtures.json`
- Чтобы остановить все контенеры
`$ docker-compose down`
- Чтобы остановить все контенеры и удалить все зависимости и сети (без образов)
`$ docker-compose down -v`
- Мониторинг запущенных контейнеров
`$ docker stats`
- Удалить все, что не используется
`$ docker system prune`

### Документация и возможности API:
К проекту подключен redoc. Для просмотра документации используйте эндпойнт `redoc/`
Пример обращения:
http://localhost/redoc/

## Разработчик:
Станислав Андрющенко