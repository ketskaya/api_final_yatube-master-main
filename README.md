# API для Yatube

## Описание
**API для Yatube** — это проект, предоставляющий интерфейс для взаимодействия с платформой Yatube. С помощью API можно публиковать записи, комментировать их, подписываться на других пользователей, а также управлять своими подписками.  
Данный проект реализован в рамках обучения и является упрощённой версией социальной сети. 

---

## Технологии
- Python 
- Django
- Django REST Framework
- Simple JWT

---

## Установка и запуск проекта

1. Клонируйте репозиторий:
   
   `git clone https://github.com/ketskaya/api_final_yatube.git`

2. Перейдите в директорию проекта:
   
   `cd api_final_yatube`

3. Создайте и активируйте виртуальное окружение:
   
   `python -m venv venv`
   
   `source venv/Scripts/activate`

5. Установите зависимости:
   
   `pip install -r requirements.txt`

6. Выполните миграции:
    
   `python manage.py migrate`

7. Запустите сервер разработки:
    
   `python manage.py runserver`

---

## Примеры запросов к API

### 1) POST-запрос: добавление комментария к публикации

`POST http://127.0.0.1:8000/api/v1/posts/12/comments/`

```
{  
  "text": "Это мой первый комментарий к посту!"  
}  
```

Ответ:
```
{  
    "id": 7,  
    "author": "admin",  
    "text": "Это мой первый комментарий к посту!",  
    "created": "2025-01-13T10:15:00Z",  
    "post": 12  
}  
```

### 2) POST-запрос: подписка на пользователя

`POST http://127.0.0.1:8000/api/v1/follow/`

```
{
  "following": "user123"
}
```

Ответ:
```
{
    "id": 5,
    "user": "admin",
    "following": "user123"
}
```

### 3) GET-запрос: получение подписок текущего пользователя

`GET http://localhost:port/api/v1/follow/`

Ответ:
```
[
    {
        "id": 5,
        "user": "admin",
        "following": "user123"
    },
    {
        "id": 6,
        "user": "admin",
        "following": "john_doe"
    }
]
```
