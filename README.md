# django-base-settings

Виртуальное окружение, которое можно создать с помощью pip + venv или Poetry:
----

* pip + venv — более привычный вариант, большая часть проектов работает в такой связке.
 
* Poetry — современный вариант, более удобный в плане отслеживания зависимостей и работы над запуском исходного кода.
 

Для создания директории проекта и виртуального окружения используются команды:
----

```python
mkdir project      #  — создаем новую директорию для проекта.
cd project      # — переходим в созданную директорию.
python -m venv env      #  — создаем виртуальное окружение.

source env/bin/activate
 #активируем виртуальное окружение (для Windows команда будет выглядеть 
env\Scripts\activate
 #или 
env\Scripts\activate.bat

pip install django    #— устанавливаем пакет Django.

pip freeze >  requirements.txt    # — сохраняем список зависимостей.
```

После создания виртуального окружения создайте проект с помощью команды:

```python
django-admin startproject config .
```

Также проект можно создавать не внутри директории, а положиться на утилиту, и тогда она создаст папку с проектом:

```python
django-admin startproject myproject
```

Для создания нового приложения используется команда:

```python
python manage.py startapp <app_name>

python manage.py runserver  # Запустить проект
```

Где 
<app_name> — название приложения, которое нужно создать.



**Описать статику:**
```python
# settings.py
STATICFILES_DIRS = (
    BASE_DIR / 'static',
)
```

**Добавить новое приложение в проект:**
```python
# settings.py
INSTALLED_APPS = [
    ...

    'new_application',
]
```


**Отправить форму методом POST:**
```python
# index.html
<form method="post">
	...
</form>
```

**Описать контроллер:**
```python
# views.py
def index(request):
    return render(request, 'main/index.html')
```



Подключение к Базе данных
----
Для того чтобы использовать PostgreSQL, в первую очередь необходимо установить специальный пакет, который отвечает за подключение Python-кода к БД:
```python
pip install psycopg2-binary   #В некоторых системах пакет может называться psycopg2
```



Настройки для подключения в проекте Django будут выглядеть так:
```python
# settings.py
...
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'db_name', # Название БД
        'USER': 'postgres', # Пользователь для подключения
        'PASSWORD': 'secret', # Пароль для этого пользователя
        'HOST': '127.0.0.1', # Адрес, на котором развернут сервер БД
        'PORT': 5432, # Порт, на котором работает сервер БД
    }
}
```
