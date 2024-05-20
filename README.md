<div id="header" align="center">
  <h1>Проект Favorite_Pets</h1>
</div>

## Что это за проект, какую задачу он решает, в чём его польза:
> [!NOTE]
> Favorite_Pets — социальная сеть для обмена фотографиями любимых питомцев.

## Как развернуть проект на локальной машине:
> [!IMPORTANT]
> * [1] (Клонируем проект) :git clone git@github.com:OsKaLis/favorite-pets.git
> * [2] (Переходим в директорию проекта) :cd favorite-pets/
> * [3] (Создание файла с настройками ".env"):
>   ```
>   POSTGRES_DB=[{Своё значение название базы}]
>   POSTGRES_USER=[{Своё значение имя пользователя для подключения к базе}]
>   POSTGRES_PASSWORD=[{Своё значение пароля для базы}]
>   DB_NAME=[{Своё значение название базы}]
>   # Добавляем переменные для Django-проекта:
>   DB_HOST=db
>   DB_PORT=5432
>   SECRET_KEY=[{Своё значение key}]
>   DEBUG=False
> * [4] (Установка docker для Windows) https://learn.microsoft.com/ru-ru/windows/wsl/install
> * [5] (Установка dpcker для Linux):
>   ``` 
>   [1] sudo apt update
>   [2] sudo apt install curl
>   [3] curl -fSL https://get.docker.com -o get-docker.sh 
>   [4] sudo sh ./get-docker.sh
>   [5] sudo apt-get install docker-compose-plugin
>   [6] sudo systemctl status docker
>   systemctl — программа, контролирующая работу системных демонов
>   status docker — команда, проверяющая статус демона Docker
> * [6] (Запуск проекта)
>   ```
>   [1] (Запускаем основные контейнеры): sudo docker compose up -d
>   [2] (Выполняет миграции и сбор статики):
>   [3] sudo docker compose exec backend python manage.py migrate
>   [4] sudo docker compose exec backend python manage.py collectstatic
>   [5] sudo docker compose exec backend cp -r /app/collected_static/. /backend_static/static/
> * [7] (Главная адрес проекта): http://127.0.0.1:9000/
> * [8] (API адрес проекта) :http://127.0.0.1:9000/api/
> * [9] (Админка проекта) :http://127.0.0.1:9000/admin/

## Cтек технологий:
<img src="https://img.shields.io/badge/Python_-3.9.10-Green">  <img src="https://img.shields.io/badge/SQLite_-3.41.2-steelblue">  <img src="https://img.shields.io/badge/django_-3.2.3-Green">
<img src="https://img.shields.io/badge/djangorestframework_-3.12.4-Green">  <img src="https://img.shields.io/badge/React_-17.0.2-aqua">  <img src="https://img.shields.io/badge/nginx:_-1.22.1-black">
<img src="https://img.shields.io/badge/docker_-24.0.5-blue">  <img src="https://img.shields.io/badge/docker_compose_-3.0-blue">  <img src="https://img.shields.io/badge/gunicorn_-20.1.0-Green">

## Некоторые примеры запросов к api_final.

### Запрос ковсем постам созданые на этом сервере, [GET] :https://cat-lovers.ru/api/cats/

### Создание новый пост авторизованным пользователем, [POST] :https://cat-lovers.ru/cats/add/
```
rew JSON:
{
    "name": "Vasyka",
    "color": "#FFFFFF",
    "birth_year": 2020,
    "owner": 5,
    "achievements": [],
    "image": null
}
```

### Создание токена, [POST] : https://cat-lovers.ru/api/token/login/
```
rew JSON:
{
    "username": "lisa",
    "password": "sFPRojyq"
}
```

## Автор: Юшко Ю.Ю.
