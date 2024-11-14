# API для Yatube
Проект api_final_yatube

Учебный проект Яндекс.Практикум курса Python-разработчик(backend).

## Технологии

    Python 3.9
    Django 3.2
    Django REST framework 3.12


## Инструкция для пользователей Git Bash

1.Клонировать репозиторий и перейти в папку **api_final_yatube**:

        git clone git@github.com:Rodomir117/api_final_yatube.git
        cd api_yatube

2.Cоздать и активировать виртуальное окружение:

        py -m venv venv
        source venv/Scripts/activate

3.Установить зависимости из файла requirements.txt:

        pip install -r requirements.txt

5.Перейти в папку проекта **yatube_api** и запустить его:

        cd yatube_api
        ./manage.py migrate
        ./manage.py runserver

6.Перейти на страницу документации проекта:

        http://127.0.0.1:8000/redoc/


## Некоторые примеры запросов к API:

- Неавторизированный пользователь
  - Получить список всех публикаций.
    - `GET api/v1/posts/`
  - _При указании параметров limit и offset выдача должна работать с пагинацией_
    - `GET /api/v1/posts/?limit=5&offset=3`
  - Получить публикацию по `id`.
    - `GET api/v1/posts/{id}/`
  - Получить все комментарии к публикации `post_id`.
    - `GET api/v1/posts/{post_id}/comments/`
  - Получить список доступнных групп.
    - `GET api/v1/groups/`   
 
- Авторизированный пользователь
  - Добавление публикации.
    - `POST /api/v1/posts/`
    - Тело запроса
      ```json
        {
        "text": "string",
        "image": "string",
        "group": 0
        }
      ```
  - Обновление публикации по `id`.
    - `POST /api/v1/posts/{id}/`
    - Тело запроса
      ```json
        {
        "text": "new_string",
        "image": "new_string",
        "group": 1
        }
      ```
  - Удаление публикации по `id`.
    - `DELETE /api/v1/posts/{id}/`
  - Подписка **на пользователя** переданного в теле запроса.
    - `POST /api/v1/follow/`
    - Тело запроса
      ```json
        {
        "following": "username_string"
        }
      ```
  - Получить список всех подписок на других пользователей.
    - `GET api/v1/follow/`