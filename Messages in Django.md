# Passing a Message/Alerts using Django and Bookstrap
https://getbootstrap.com/docs/5.3/components/alerts/#dismissing : Bootstrap Alerts Link<br>
https://docs.djangoproject.com/en/4.2/ref/contrib/messages/: Django Messages Documentation
```
<!-- Loading bootstrap **5.3.0** via CDN -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-9ndCyUaIbzAi2FUVXJi0CjmCapSmO7SnpJef0486qhLnuZ2cdeRhO02iuK6FUUVM" crossorigin="anonymous">
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js" integrity="sha384-geWF76RCwLtnZ8qwWowPQNguL3RmwHVBC9FhGdlKrxdiJJigb/j/68SIy3Te4Bkz" crossorigin="anonymous"></script>
```
Attach the above code in ```base.html``` as we want we display the Alerts below the **navbar** whenever needed.<br>
```base.html``` is the common template that can be reused multiple times using ```{% extends 'base.html' %}```<br>

```
      {% if messages %}
      {% for message in messages %}
        <div class="alert alert-{{ message.tags }} alert-dismissible fade show" role="alert">
          <strong>Hello there!</strong> {{message}}
          <button type="button" class="btn-close" data-bs-dismiss="alert" aria-label="Close"></button>
        </div>
      {% endfor %}
      {% endif %}
#base.html
```
:bangbang:The  ```tags``` from ```messages.{tags}(request,"msg")``` in ```views.py``` will be passed in ``` alert-{{ message.tags }}``` so that the color change happens accordingly<br>
:bangbang:The div is from Bootstrap and the ```if``` & ```for``` is from ```Django messages```<br>


![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/a0d30be3-0f7a-49d1-9b3e-4909e373b0f5)

# From Bootstrap
**Dismissing Alerts:** 
Using the alert JavaScript plugin, it’s possible to dismiss any alert inline. Here’s how:<br>
+ Be sure you’ve loaded the *alert* plugin, or the compiled Bootstrap JavaScript.<br>
+ Add a close button and the *.alert-dismissible* class, which adds extra padding to the right of the alert and positions the close button.<br>
+ On the close button, add the *data-bs-dismiss="alert"* attribute, which triggers the JavaScript functionality. Be sure to use the <button> element with it for proper behavior across all devices.<br>
To animate alerts when dismissing them, be sure to add the *.fade* and *.show* classes<br>

![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/fe814628-404c-4dd3-a419-461d5dd026ff)

https://docs.djangoproject.com/en/4.2/ref/contrib/messages/#:~:text=Adding%20a%20message,classes%20for%20the%20message)%3A

This is where the message is passed ```messages.{tag}(request,"Msg")```<br>
The possible ```Tags``` from Django are:<br>

![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/046892f4-5c25-48a6-a52c-a135bd16a132)

+ This ```tags``` will be passed in ``` alert-{{ message.tags }}``` so that the color change happens accordingly<br>

## Problem with Danger-Error

![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/bda2b350-e6c1-4cb6-9f5e-8ce04cff44d9)

## The Solution

+ Adding the folowing in  ```setting.py```
```
from django.contrib.messages import constants as messages

MESSAGE_TAGS = {
    messages.ERROR: 'danger'
}
#Here we are making a addition in ERROR 'Level Constant' and making 'danger' into it as Bootstrap reads danger as critical
```
:bangbang: Now, while passing messages.{tags} in ```views.py``` pass<br> ```messages.error(request,"Plz Correctly fill the form.....")```<br>
<br>**OR**<br>
+ A suggested workaround for this name clash is: keep the Django template tag unchanged, which will give the element a class called alert-error. Then use a couple of lines of Javascript somewhere in your HTML template to add alert-danger as an extra class to these elements:
+ This will add the class 'alert-danger' to elements which have the class 'alert-error'. 'alert-error' will be ignored by Bootstrap, but with 'alert-danger' added to the elements' class lists, they will get Bootstrap's red contextual formatting.
```
// Javascript somewhere in your HTML template
let errorElements = document.getElementsByClassName('alert-error');
[...errorElements].forEach(el => {el.classList.add('alert-danger')});
```
:bangbang: Reference: https://stackoverflow.com/questions/44251583/django-allauth-custom-messages-styling-messages-with-html-css 


