# Creating a virtual env
```python -m venv "name"```
## Running the env
```.\{name}\Scripts\activate``` and ```.\{name}\Scripts\deactivate``` to deactivate
# Starting a Project
```django-admin startproject {name}```
Here it's text
# Starting a app
```django-admin startapp {name} ``` <br>
Here its ct

### Inside the project module
Go to ```urls.py``` <br>
```
from django.contrib import admin
from django.urls import path,include

urlpatterns = [
    path("admin/", admin.site.urls),
    path("",include("ct.urls")),
]
```
then go inside the app and create a ```urls.py``` <br>
```
from django.urls import path
from ct import views

urlpatterns = [
    path("",views.home),
]
```
+ There is only ONE static  &  templates folder in the dir where manage.py exists
+ Create Models to have a Database which we can access using /admin 
+ To link CSS and JS in html ------>>>>
### in setting.py
Add ```STATICFILES_DIRS= (os.path.join(BASE_DIR,'static'),)``` <br>
Keep the CSS & JS file in static folder <br>
in the html file add ```{% load static %}```<br>
and it with ```<link rel="stylesheet" href="{% static 'blog.css' %}">``` <br>


![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/58b8cf43-ac7f-4c5c-a61a-e354a03cb287)

# setting.py
```
TEMPLATES = [ 
    { 
    
        "BACKEND": "django.template.backends.django.DjangoTemplates", 
        "DIRS": ['templates'], ### IMPORTANT to include template folder where the html css files will be kept 
        "APP_DIRS": True, 
        "OPTIONS": .....
            ],
        },
    },
]
```
+ python manage.py makemigrations : is for saving changes made 
+ python manage.py migrate is for uploading the changes in the database

## Create a Model in model.py in the app
> Here, name of the DataBase in 'Contact'
```
from django.db import models
class Contact(models.Model):
    SIno =models.AutoField(primary_key=True) 
    Name=models.CharField(max_length=70) 
    Phone=models.CharField(max_length=13) 
    Email=models.CharField(max_length=30) 
    Content=models.TextField(max_length=400) 
    time=models.DateTimeField(auto_now_add=True,blank=True)
```
Now run the following in terminal to store the changes:
``` python manage.py makemigrations```

**Then**

### Register that class in admin.py in app 

```
from django.contrib import admin
from .models import Contact
admin.site.register(Contact)

INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
    
    "blog.apps.BlogConfig",#From apps.py we get 'BlogConfig'  ////////// Without changing this in INSTALLED_APPS , migrations wont be possible
]

```

### IMP to add in setting.py --> INSTALLED_APPS
+ {appname}.apps.{ClassName from apps.py} 
```
 "blog.apps.BlogConfig", #From apps.py we get 'BlogConfig'  ////////// Without changing this in INSTALLED_APPS , migrations wont be possible
```
Now,Run the following
```python manage.py migrate```

## The model/Database can be accessed from /admin now
