![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/34f57205-c0d5-4c34-9f3a-2afed2204b88)Here ```mysite``` is the folder we get after we ```startproject``` in Django<br>

Important to include ```from django.urls import path,include```<br>

In ```urls.py``` we set all route to respective apps using ```path({routeName}/,include("{appName}.urls"))``` <br>

Here, We have two apps ```blog``` & ```shop``` (A Django project can have multiple apps) <br>

![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/e633c5f5-609d-4151-8be6-2d8337ffd966)

From Here,Routes are managed from ```urls.py``` of the Respective app,eg: ```Blog``` / ```shop```<br>
Say,```http://127.0.0.1:8000/shop/``` onwards *Routes* will be set by ```urls.py``` of ```shop``` dir<br>

## Routes of "blog" app
We use the ```urls.py``` to define all routes of the app<br>

![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/779e38df-6a7f-4d4a-babf-fd2bd08ab322)

So, for ```/contact/``` ```views.contact``` will be responsible,i.e, 

## The "views.py" of the app "blog"
The ```views.py``` of a app is where we define how and what will take place eg, ```HttpResponse(request,"msg")``` or ```render(request,"filename.html")```<br>

![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/898aad1f-ebbd-4e2a-a33e-920a9e9956fa)

:bangbang: **template** is the folder where all the ```.html``` files are kept. It is placed in same directory as ```manage.py```.There is only 1 ```template``` folder in whole project<br>
:bangbang: **static** is the file where all **static** elements are kept like **images**.It is placed in same directory as``` manage.py```.There is only 1 ```static``` folder in whole project<br>
:pushpin: Here we,returned ```return render(request,'blog/about.html')``` as our ```template``` folder has a subfolder ```blog```.
