
## Instructions to create Hello World Django application
1. Verify whether Django is installed or not by using the command "python -m django --version". After running the command in python code you will see version '5.0.4'. If version is not shownig any output , then you need to install Django by using the command "python -m pip install Django".

2. After installation, you have to create a django project by using the command "django-admin startproject mysite". In current location where you run the command there created a folder mysite which contains the files as shown below.
```
mysite/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        asgi.py
        wsgi.py
```
3. Now run the command "python manage.py runserver "python manage.py runserver" it displays the output as follows:

```
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).

You have 18 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions.
Run 'python manage.py migrate' to apply them.
April 21, 2024 - 09:38:28
Django version 5.0.4, using settings 'mysite.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.
```
4. Now open the url "http://127.0.0.1:8000/" in web browser. it shows the output "Congratulations!"
5. Now run the command inside mysite folder which was created earlier ,"python manage.py startapp polls" to create a polls app. By running the command you observed a folder named "polls" inside mysite folde. In that folder you observed files listed below
```
polls/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests.py
    views.py
```
6. Now add the below python code in polls/views.py python file
```python
from django.shortcuts import render
from django.http import JsonResponse

# Create your views here.

def index(request):
    return JsonResponse({'Message': 'Hello World!'})
```
7. After that you need to create a urls.py python file in polls folder and add the below python code.
```python
from django.urls import path

from . import views

urlpatterns = [
    path("", views.index, name="index"),
]
```
8. Now in mysite/urls.py python file and add the below code.
```python
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path("polls/", include("polls.urls")),
    path("admin/", admin.site.urls),
]
```
9. Now run the command "python manage.py runserver" then visit the url "http://localhost:8000/polls/". After opening the url in browser you can see the output in json format as shown below:
{"Message": "Hello World!"}
