# Ex.05 Design a Website for Server Side Processing
## Date:
21-12-2024
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
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Power Calculator</title>
</head>
<body>
    <div>
        <center><div class="one"><h1>POWER CALCULATOR</h1></div>
            <form align="center" method="POST">
                {% csrf_token %}
                Intensity <input name="I" value="{{i}}">
                <br>
                <br>
                Resistance <input name="R" value="{{r}}">
                <br>
                <br>
                <input type="submit" value="calculate">
                <br>
                <br>
                Power <input name="power"value={{power}}>
            </form>
        </center>
    </div>
</body>
</html>

views.py

from django.shortcuts import render 
def powerofbulb(request): 
    context={} 
    context['power'] = "0" 
    context['i'] = "0" 
    context['r'] = "0" 
    if request.method == 'POST': 
        print("POST method is used")
        i = request.POST.get('I','0')
        r = request.POST.get('R','0')
        print('request=',request) 
        print('Intensity=',i) 
        print('Resistance=',r) 
        power = (int(i) ** 2)*int(r) 
        context['power'] = power 
        context['i'] = i
        context['r'] = r
        print('power=',power) 
    return render(request,'mathapp/math.html',context)

    urls.py

    from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('powerofbulb/',views.powerofbulb,name="powerofbulb"),
    path('',views.powerofbulb,name="powerofbulbroot")
]

```

## SERVER SIDE PROCESSING:
![alt text](<Screenshot 2024-12-21 205954-1.png>)

## HOMEPAGE:
![alt text](<Screenshot 2024-12-21 210124-2.png>)

## RESULT:
The program for performing server side processing is completed successfully.
