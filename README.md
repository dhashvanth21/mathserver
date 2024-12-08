# Ex.05 Design a Website for Server Side Processing
# Date: 30/11/2024
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```
math.html

{%load static%}

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Incandescent Bulb Power Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #1d1d1f;
            color: #333;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .calculator {
            background-color: #fff;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
            width: 300px;
            text-align: center;
        }
        h1 {
            color: #5fc5f4;
            font-size: 24px;
        }
        input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
        }
        button {
            background-color: #58b1da;
            color: white;
            padding: 10px;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
        }
        button:hover {
            background-color: #3d72dc;
        }
        .result {
            font-size: 20px;
            color: #333;
            margin-top: 20px;
        }
    </style>
</head>
<body>

    <div class="calculator">
        <form method="POST">
            {% csrf_token %}
        
        <h1>Power Calculator</h1>
        <label for="intensity">Intensity (I in Amps):</label>
        <input type="number" name='intensity' id="intensity" value="{{i}}" placeholder="Enter Intensity (I)" required>

        <label for="resistance">Resistance (R in Ohms):</label>
        <input type="number" name="resistance"  id="resistance" value="{{r}}"placeholder="Enter Resistance (R)" required>
        <button type="submit">Calculate Power</button>
        <input type="text" placeholder="Power" id="power" name="power" value="{{power}}">

        </form>
    </div>


</body>
</html>

views.py
from django.shortcuts import render
def powerlamp(request): 
    context={} 
    context['power']="0" 
    context['i']="0" 
    context['r']="0" 
    if request.method=='POST': 
        print("POST method is used")
        i=request.POST.get('intensity','0')
        r=request.POST.get('resistance','0')
        print('request=',request) 
        print('intensity=',i) 
        print('resistance=',r) 
        power=(int(i) ** 2 ) * int(r) 
        context['power']=power
        context['i']=i
        context['r']=r 
        print('Power=',power) 
    return render(request,'msapp/vijay.html',context)

urls.py
from django.contrib import admin 
from django.urls import path 
from maths import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('powerlamp/',views.powerlamp,name="powerlamp"),
    path('',views.powerlamp,name="powerlamproot")
]
```
# SERVER SIDE PROCESSING:
![image](https://github.com/user-attachments/assets/f59e4282-7b8c-4ec3-b214-deb1373c77f7)

# HOMEPAGE:
![image](https://github.com/user-attachments/assets/79186d97-ec94-4898-ae0c-491f3db772ef)

# RESULT:
The program for performing server side processing is completed successfully.
