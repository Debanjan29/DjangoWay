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
