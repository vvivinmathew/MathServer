# Ex.05 Design a Website for Server Side Processing
## Date:2/12/2024

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
<html>
<head>
<style>
    body 
{
background-color:white;
}
.edge {
height: 100%;
display:flex;
justify-content:center;
align-items: center;
}
.box {
display:block;
border:blue;
width: 500px;
height: 300px;
font-size: 20px;
background-color:grey;
}
.formelt{
color:pink;
text-align: center;
margin-top: 7px;
margin-bottom: 6px;
}
h1
{
color:green;
text-align: center;
padding-top: 20px;
}
</style>
</head>
<body>
<div class="edge">
<div class="box">
<h1>Power of a Light Filament</h1>
<h2>VIVIN MATHEW(24001048)</h2>
<form method="POST">
{% csrf_token %}
<div class="formelt">
Intensity : <input type="text" name="intensity" value="{{i}}"></input>(in Wm<sup>-2</sup>)<br/>
</div>
<div class="formelt">
Resistance : <input type="text" name="resistance" value="{{r}}"></input>(in ohm)<br/>
</div>
<div class="formelt">
<input type="submit" value="Calculate"></input><br/>
</div>
<div class="formelt">
Power : <input type="text" name="power" value="{{power}}"></input>(in W)<br/>
</div>
</form>
</div>
</div>
</body>
</html>

views.py

from django.shortcuts import render 
def power(request): 
    context={} 
    context['power'] = "0" 
    context['i'] = "0" 
    context['r'] = "0" 
    if request.method == 'POST': 
        print("POST method is used")
        i = request.POST.get('intensity','0')
        r = request.POST.get('resistance','0')
        print('request=',request) 
        print('Intensity=',i) 
        print('Resistance=',r) 
        power = int(i) * int(i) * (int(r)) 
        context['power'] = power 
        context['i'] = i
        context['r'] = r 
        print('Power=',power) 
    return render(request,'mathapp/mathew.html',context)

urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('math/',views.power,name="math"),
    path('',views.power,name="mathroot")
]



```

## SERVER SIDE PROCESSING:
![alt text](<Screenshot 2024-12-09 230652.png>)

## HOMEPAGE:
![alt text](<Screenshot 2024-12-09 230629.png>)

## RESULT:
The program for performing server side processing is completed successfully.
