## YaMDb
### Описание
Проект YaMDb собирает отзывы пользователей на произведения. Произведения делятся на категории: «Книги», «Фильмы», «Музыка».
### Технологии
python 3.9.6  
django 3.0.5  
gunicorn 20.1.0  
### Проект доступен по ссылке :
http://84.201.181.59/api/v1/

![yamdb-final workflow](https://github.com/lindex/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
<<<<<<< HEAD
#######

## Описание Workflow

##### Workflow состоит из четырёх шагов:

1. Проверка кода на соответствие PEP8, запуск тестов проекта.
2. Сборка и публикация образа на DockerHub.
3. Автоматический деплой на выбранный сервер.
4. Отправка ботом уведомления в телеграм-чат.


## Подготовка и запуск проекта
##### Клонирование репозитория
```bash
git clone https://github.com/lindex/yamdb_final.git
```

## Установка на удаленном сервере (Ubuntu):
##### Шаг 1. Вход на удаленный сервер
Подключаемся на удаленный сервер
```bash
ssh <username>@<ip_address>
```

##### Шаг 2. Установка docker:

```bash
sudo apt install docker.io 
```

##### Шаг 3. Установка docker-compose:

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

##### Шаг 4. Копирование docker-compose.yaml и nginx/default.conf:
Скопируйте подготовленные файлы `docker-compose.yaml` и `nginx/default.conf` из проекта на сервер в `home/<ваш_username>/docker-compose.yaml` и `home/<ваш_username>/nginx/default.conf` соответственно.


```bash
scp docker-compose.yaml <username>@<host>:/home/<username>/docker-compose.yaml
scp -r nginx/ <username>@<host>:/home/<username>/
```

##### Шаг 5. Добавление Github Secrets:
Для работы с Workflow добавьте в Secrets GitHub переменные окружения для работы:
```bash
SECRET_KEY=<SECRET_KEY>
DEBUG=<True/False>
ALLOWED_HOSTS=<hosts>

DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432

DOCKER_PASSWORD=<pass DockerHub>
DOCKER_USERNAME=<login DockerHub>

USER=<username для подключения к серверу>
HOST=<IP сервера>
PASSPHRASE=<passphrase для сервера, если он установлен>
SSH_KEY=<SSH ключ>

TELEGRAM_TO=<ID своего телеграм-аккаунта. Для инфо @myidbot>
TELEGRAM_TOKEN=<токен бота>
```

##### Шаг 6. После успешного деплоя:

###### Создаем и применяем миграции:
```bash
sudo docker-compose exec web python manage.py makemigrations --noinput
sudo docker-compose exec web python manage.py migrate --noinput
```
###### Подгружаем статику
```bash
sudo docker-compose exec web python manage.py collectstatic --no-input 
```
###### Заполняем базу данных:
```bash
sudo docker-compose exec web python3 manage.py loaddata fixtures.json
```
###### Созlдаем суперпользователя Django:
```bash
sudo docker-compose exec web python manage.py createsuperuser
```
### Участники
студенты курса Python-разработчик в Яндекс.Практикуме
- [lindex](https://github.com/lindex/) - Марк
[mitya888](https://github.com/mitya888/) - Дмитрий
=======
######
>>>>>>> parent of 1d12bed (Update README.md)
