
Here, we have contact.html which is the page one gets to see when we goes to ```/contact``` <br>
In ```<form action="/contact/" method="post">```<br>
```form action="/contact/``` means that when the form is submited it redirects to ```/contact``` <br>
```method="post"``` ,means a POST Request will take place twhen the form is Submitted 

<br>

![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/b6af4009-0c89-4d01-ad33-aca401abb88d)

## STEP 2:
The ```models.py``` file<br>

![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/4cb6857f-0ddd-44c9-bc1e-e5165a95a40c)

## STEP 3:
The ```views.py``` file<br>
From ```models.py``` import the Class<br>
```from . models import Contact```

We send a request from the Frontend which we check using
```if request.method=="POST":```

Now to access the Data sent from Frontend we use
```request.POST["{name of the input type that is given .html file}"```
Eg:<br>

![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/fb4ddcd0-6cd3-4fd6-8aaf-7c821ea034f1)<br>

# Now we create a few Varible to the Data from the Frontend
```
def contact(request):
     if request.method=="POST":
          name=request.POST["name"]
          email=request.POST["email"]
          phone=request.POST["phone"]
          msg=request.POST["content"]
```
# Now to need to send these Data in Database
In ```models.py``` we had *class Contact* which makes the ```Fields``` in the Database<br>
We, send our **Input Data** into those **Database Field** with the help of Object Calling<br>

```Var={ClassName}( {DatabaseField = Variable,... } )```<br>
```Var.save()```

```
contact_variable=Contact(Name=name,Phone=phone,Email=email,Content=msg) # contact_variable is a variable which is used to store the result of Object Calling 'Contact'
contact_variable.save()
```

Now reload the server and Input the form<br>
The *django admin* shows a msg like <br> 
![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/6e44af69-fdb4-48d8-b9d2-e97d327a78c8)

This can be Imporved by adding the following in class Contact (In this example) in ```models.py```
```
def __str__(self):
    return "From "+ self.Name + "" + self.Email
```

Here, we have contact.html which is the page one gets to see when we goes to ```/contact``` <br>
In ```<form action="/contact/" method="post">```<br>
```form action="/contact/``` means that when the form is submited it redirects to ```/contact``` <br>
```method="post"``` ,means a POST Request will take place twhen the form is Submitted 

<br>

![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/b6af4009-0c89-4d01-ad33-aca401abb88d)

## STEP 2:
The ```models.py``` file<br>

![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/4cb6857f-0ddd-44c9-bc1e-e5165a95a40c)

## STEP 3:
The ```views.py``` file<br>
From ```models.py``` import the Class<br>
```from . models import Contact```

We send a request from the Frontend which we check using
```if request.method=="POST":```

Now to access the Data sent from Frontend we use
```request.POST["{name of the input type that is given .html file}"```
Eg:<br>

![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/fb4ddcd0-6cd3-4fd6-8aaf-7c821ea034f1)<br>

# Now we create a few Varible to the Data from the Frontend
```
def contact(request):
     if request.method=="POST":
          name=request.POST["name"]
          email=request.POST["email"]
          phone=request.POST["phone"]
          msg=request.POST["content"]
```
# Now to need to send these Data in Database
In ```models.py``` we had *class Contact* which makes the ```Fields``` in the Database<br>
We, send our **Input Data** into those **Database Field** with the help of Object Calling<br>

```Var={ClassName}( {DatabaseField = Variable,... } )```<br>
```Var.save()```

```
contact_variable=Contact(Name=name,Phone=phone,Email=email,Content=msg) # contact_variable is a variable which is used to store the result of Object Calling 'Contact'
contact_variable.save()
```

Now reload the server and Input the form<br>
The *django admin* shows a msg like <br> 
![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/6e44af69-fdb4-48d8-b9d2-e97d327a78c8)

This can be Imporved by adding the following in class in ```models.py```
```
def __str__(self):
    return "From "+ self.Name + "" + self.Email
```
![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/b040c466-4d00-45b8-9db7-870e859cd35f)

## The Results

![image](https://github.com/Debanjan29/DjangoWay/assets/97180277/de60413f-e5ff-4fed-b808-d43e82933920)





















