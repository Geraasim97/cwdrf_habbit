[tool.poetry]
name = "cwdrf"
version = "0.1.0"
description = ""
authors = ["gerasimov nikita <geraasim97@mail.ru>"]
readme = "README.md"
packages = [{include = "habit_tracker_cw7"}]

[tool.poetry.dependencies]
python = "^3.11"
poetry = "^1.6.1"
django = "^4.2.6"
psycopg2-binary = "^2.9.9"
python-dotenv = "^1.0.0"
djangorestframework = "^3.14.0"
djangorestframework-simplejwt = "^5.3.0"
django-filter = "^23.3"
celery = "^5.3.4"
redis = "^5.0.1"
django-celery-beat = "^2.5.0"
requests = "^2.31.0"
drf-yasg = "^1.21.7"
django-cors-headers = "^4.3.0"
coverage = "^7.3.2"
flake8 = "^6.1.0"


[build-system]
requires = ["poetry-core"]
build-backend = "poetry.core.masonry.api"
Трекер полезных привычек

Цель проекта заключается в создании бэкенд-части SPA веб-приложения, 
которая позволяет пользователям приобретать новые полезные привычки.


Установка и использование

Для работы программы необходимо установить зависимости, указанные в файле pyproject.toml.

Заполнить файл .env своими данными (на примере файла .env.sample).

В файле settings.py необходимо указать адреса frontend-серверов в разделе CORS

Сделать миграции.

Запустить задачу по рассылке уведомлений:

celery -A config worker -l info
celery -A config beat -l info -S django


Описание приложений

- main - отвечает за создание и управление привычками, местами выполнения привычек, вознаграждениями за привычки

- users - отвечает за регистрацию и авторизацию пользователей сайта


Дополнительная информация

- tasks.py(main) - содержит периодическую задачу по рассылке уведомлений о наступлении времени выполнения привычки в telegram

- Настроен вывод документации.


Рекомендации пользователям по получению telegram-рассылок:
1) При регистрации необходимо указать chat_id, который можно получить с помощью @getmyid_bot. 
Для этого необходимо добавить данный аккаунт в телеграм и выполнить команду /start
2) Для того чтобы наш бот имел возможность рассылать вам сообщения, необходимо добавить бота в "контакты" телеграмм
и выполнить команду /start