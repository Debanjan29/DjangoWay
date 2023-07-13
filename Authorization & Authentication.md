The Django authentication system handles both authentication and authorization. Briefly, authentication verifies a user is who they claim to be, and authorization determines what an authenticated user is allowed to do. Here the term authentication is used to refer to both tasks.

The auth system consists of: <br>
Users <br>
Permissions: Binary (yes/no) flags designating whether a user may perform a certain task. <br>
Groups: A generic way of applying labels and permissions to more than one user. <br>
A configurable password hashing system <br>
Forms and view tools for logging in users, or restricting content <br>
A pluggable backend system <br>

Django has a ready made ```User``` Database which can be used. <br>
In ```views.py``` <br>
```from django.contrib.auth.models import User``` <br>

Pushing the Inputs into Database <br>
```
user=User.objects.create_user(username=user,email=email,password=passw1)
user.first_name=Fname
user.last_name=Lname
user.save()
```
Django Documentation: https://docs.djangoproject.com/en/4.2/topics/auth/default/

### Views.py
![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/996e7624-a408-4498-95fb-d0201faf5d51)

### base.html
![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/9bca6d96-a89c-4d10-b925-4053e8c3a3c4)
