# Проект Reviews

Сервис Reviews — база отзывов о различных произведениях.

Это совместный проект и настоящая командная работа трёх студентов на Яндекс.Практикум.

### Настроен CI/CD

Запуск Flake8 и тестов, обновление образа DockerHub, деплой на сервер.

![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white)
 ![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white) ![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white) ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![DjangoREST](https://img.shields.io/badge/DJANGO-REST-ff1709?style=for-the-badge&logo=django&logoColor=white&color=ff1709&labelColor=gray) ![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white) 

## Описание проекта

API для сервиса Reviews.

**Отзывы**: получить список всех отзывов, создать новый отзыв, получить отзыв по id, частично обновить отзыв по id, удалить отзыв по id.

**Комментарии к отзывам**: получить список всех комментариев к отзыву по id, создать новый комментарий для отзыва, получить комментарий для отзыва по id, частично обновить комментарий к отзыву по id, удалить комментарий к отзыву по id.

**JWT-токен**: отправить confirmation_code на переданный email, получение JWT-токена в обмен на email и confirmation_code.

**Пользователи**: получить список всех пользователей, создание пользователя, получить пользователя по username, изменить данные пользователя по username, удалить пользователя по username, получить данные своей учетной записи, изменить данные своей учетной записи.

**Категории (типы) произведений**: получить список всех категорий, создать категорию, удалить категорию.

**Категории жанров**: получить список всех жанров, создать жанр, удалить жанр.

**Произведения, к которым пишут отзывы**: получить список всех объектов, создать произведение для отзывов, информация об объекте, обновить информацию об объекте, удалить произведение.


## Как запустить проект на сервере с Ubuntu

Склонируйте репозиторий и перейдите в него в командной строке:

```
git clone <SSH or HTTPS>

```

Выполните вход на свой удаленный сервер

Установите docker на сервер:

```
sudo apt install docker.io
```

Установите docker-compose на сервер:

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose
```

Запустите docker-compose:

```
docker-compose up -d --build
```

Соберите файлы статики, и запустите миграции командами:

```
docker-compose exec web python3 manage.py makemigrations
```
```
docker-compose exec web python3 manage.py migrate
```
```
docker-compose exec web python3 manage.py collectstatic --no-input
```

Создайте суперпользователя командой:

```
docker-compose exec web python3 manage.py createsuperuser
```

Команда по загрузке файла fixtures в БД
```
docker-compose exec web python3 manage.py dumpdata > fixtures.json
```

Остановить можно командой:

```
docker-compose down -v
```

## Автор
Воробьёв Илья
