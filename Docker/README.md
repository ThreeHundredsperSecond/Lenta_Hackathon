# Подготовка и запуск проекта

## Клонирование репозитория
```bash
git clone git@github.com:AlexBesedin/LentaHackathon.git
```


## Создание файла с переменными окружения (.env)
`cd LentaHackathon/infra
touch .env
SECRET_KEY = <Секретный ключ>
DB_ENGINE=<django.db.backends.postgresql>
DB_NAME=<имя базы данных postgres>
DB_USER=<пользователь бд>
DB_PASSWORD=<пароль>
DB_HOST=<db>
DB_PORT=<5432>
CELERY_BROKER_URL=redis://redis:6379/0
CELERY_RESULT_BACKEND=redis://redis:6379/0`

## Развертывание контейнеров и выполнение миграций
`cd LentaHackathon/infra/
sudo docker-compose up -d --build
sudo docker-compose exec backend python manage.py migrate`


## Создание суперпользователя и сбор статики
`sudo docker-compose exec backend python manage.py createsuperuser
sudo docker-compose exec backend python manage.py collectstatic --no-input`

## Загрузка магазинов, категорий и продаж в базу данных
`sudo docker-compose exec backend python manage.py import_stores
sudo docker-compose exec backend python manage.py import_categories
sudo docker-compose exec backend python manage.py import_sales`


## Запуск задачи Celery вручную

*Примечание: Данная команда запустит инференс прогноза, который сделает запросы в базу данных, после передаст данные в DS модель, и полученный прогноз от DS модели запишет в базу данных в модель Forecast.
`sudo docker-compose exec backend celery -A lenta_main call lenta_main.tasks.main`

# На продакшене, необходимо выставить время, когда будет выполняться асинхронная задача прогноза. Выполнение задачи будет происходит в фоновом режиме.
`CELERY_BEAT_SCHEDULE = {
    'run_main_every_10_min': {
        'task': 'lenta_main.tasks.main',
        'schedule': timedelta(minutes=10),
    },
}`

##Celery Flower позволяет отслеживать состояние и прогресс выполнения задач, а также управлять задачами и рабочими процессами в вашем Celery-кластере через веб-интерфейс.

`http://localhost:5555/`


##Документация

API документация будет доступна по адресу:

`http://ваш_ip_адрес/api/docs/`
