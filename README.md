# Favorite_Pets
## Что это за проект, какую задачу он решает, в чём его польза;
```
Favorite_Pets — социальная сеть для обмена фотографиями любимых питомцев.
```

## Как развернуть проект на локальной машине.
```
1  ] (Клонируем проект) :git clone git@github.com:OsKaLis/kittygram_final.git
2  ] (водим пароль если доступ приватный)
3  ] (Переходим в директорию проекта) :cd kittygram_final/

4  ] (Установка): docker
5  ] (Установка docker для Windows) https://learn.microsoft.com/ru-ru/windows/wsl/install

6  ] (Создание файла с настройками ".env"):
```
6.1] POSTGRES_DB=[{Своё значение название базы}]
6.2] POSTGRES_USER=[{Своё значение имя пользователя для подключения к базе}]
6.3] POSTGRES_PASSWORD=[{Своё значение пароля для базы}]
6.4] DB_NAME=[{Своё значение название базы}]
6.5] # Добавляем переменные для Django-проекта:
6.6] DB_HOST=db
6.7] DB_PORT=5432
6.8] SECRET_KEY=[{Своё значение key}]
6.9] DEBUG=False
```
7  ] (Установка dpcker для Linux): 
7.1] sudo apt update
7.2] sudo apt install curl
7.3] curl -fSL https://get.docker.com -o get-docker.sh 
7.4] sudo sh ./get-docker.sh
7.5] sudo apt-get install docker-compose-plugin 
7.6] # systemctl — программа, контролирующая работу системных демонов
   ] # status docker — команда, проверяющая статус демона Docker
   ] sudo systemctl status docker 

8  ] (Запуск проекта)
8.1] (Запускаем основные контейнеры): sudo docker compose up -d
8.2] (Выполняет миграции и сбор статики):
8.3] sudo docker compose exec backend python manage.py migrate
8.4] sudo docker compose exec backend python manage.py collectstatic
8.5] sudo docker compose exec backend cp -r /app/collected_static/. /backend_static/static/

9  ] (Главная адрес проекта): http://127.0.0.1:9000/
10 ] (API адрес проекта) :http://127.0.0.1:9000/api/
11 ] (Админка проекта) :http://127.0.0.1:9000/admin/
```

## Некоторые примеры запросов к api_final.

[ Запрос ковсем постам созданые на этом сервере.]
[GET] :https://cat-lovers.ru/api/cats/

[ Создание новый пост авторизованным пользователем.]
[POST] :https://cat-lovers.ru/cats/add/
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

[ Создание токена.]
[POST] : https://cat-lovers.ru/api/token/login/
```
rew JSON:
{
    "username": "lisa",
    "password": "sFPRojyq"
}
```

## Cтек технологий:
```
1 ] Cистема управления базами данных SQLite
2 ] Язык программирования Python
3 ] Фреймворк django, rest, React
```

## Автор: Юшко Ю.Ю.


#  Как работать с репозиторием финального задания

## Что нужно сделать

Настроить запуск проекта Kittygram в контейнерах и CI/CD с помощью GitHub Actions

## Как проверить работу с помощью автотестов

В корне репозитория создайте файл tests.yml со следующим содержимым:
```yaml
repo_owner: ваш_логин_на_гитхабе
kittygram_domain: полная ссылка (https://доменное_имя) на ваш проект Kittygram
taski_domain: полная ссылка (https://доменное_имя) на ваш проект Taski
dockerhub_username: ваш_логин_на_докерхабе
```

Скопируйте содержимое файла `.github/workflows/main.yml` в файл `kittygram_workflow.yml` в корневой директории проекта.

Для локального запуска тестов создайте виртуальное окружение, установите в него зависимости из backend/requirements.txt и запустите в корневой директории проекта `pytest`.

## Чек-лист для проверки перед отправкой задания

- Проект Taski доступен по доменному имени, указанному в `tests.yml`.
- Проект Kittygram доступен по доменному имени, указанному в `tests.yml`.
- Пуш в ветку main запускает тестирование и деплой Kittygram, а после успешного деплоя вам приходит сообщение в телеграм.
- В корне проекта есть файл `kittygram_workflow.yml`.
