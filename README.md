# Ex.05 Design a Website for Server Side Processing
## Date:12/04/2024

## AIM:
To design a website to find surface area of a Right Cylinder in server side.

## FORMULA:
Surface Area = 2Πrh + 2Πr<sup>2</sup>
<br>r --> Radius of Right Cylinder
<br>h --> Height of Right Cylinder

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
## math.py
```
<html>

<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>Surface Area of Right Cylinder</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <style type="text/css">
        body {
            background-color: rgb(189, 198, 221);
        }

        .edge {
            display: flex;
            height: 100vh;
            width: 100%;    
            justify-content: center;
            align-items: center;
        }

        .box {
            display: block;
            width: 500px;
            min-height: 300px;
            font-size: 20px;
            background: rgb(7,85,152);
            background: linear-gradient(90deg, rgba(7,85,152,1) 9%, rgba(7,142,150,1) 56%);
            border-radius: 10px;
            box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
        }

        .formelt {
            color: whitesmoke;
            text-align: center;
            margin-top: 7px;
            margin-bottom: 6px;
        }

        h1 {
            color: white;
            text-align: center;
            padding-top: 20px;
        }
        input{
            margin: 5px;
            padding: 5px;
            border-radius: 5px;
            border: none;

        }
    </style>
    
</head>

<body>
    <div class="edge">
        <div class="box">
            <h1>Surface Area of Right Cylinder</h1>
            <form method="POST">
                {% csrf_token %}
                <div class="formelt">
                    Radius : <input type="text" name="radius" value="{{r}}"></input>(in m)<br />
                </div>
                <div class="formelt">
                    Height : <input type="text" name="height" value="{{h}}"></input>(in m)<br />
                </div>
                <div class="formelt">
                    <input type="submit" value="Calculate"></input><br />
                </div>
                <div class="formelt">
                    Surface Area : <input type="text" name="area" value="{{area}}"></input>m<sup>2</sup><br />
                </div>
            </form>
        </div>
    </div>
</body>

</html>

```
## views.py
```
from django.shortcuts import render

# Create your views here.
def surfacearea(request):
    context={}
    context['area'] = "0"
    context['r'] = "0"
    context['h'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        r = request.POST.get('radius','0')
        h = request.POST.get('height','0')
        print('request=',request)
        print('Radius=',r)
        print('Height=',h)
        area = 2*(3.14)*int(r)*int(h) + 2*(3.14)*int(r)*int(r)
        context['area'] = area
        context['r'] = r
        context['h'] = h
        print('Area=',area)
    return render(request,'index.html',context)

```
## urls.py
```
"""
URL configuration for project2 project.

The `urlpatterns` list routes URLs to views. For more information please see:
    https://docs.djangoproject.com/en/5.0/topics/http/urls/
Examples:
Function views
    1. Add an import:  from my_app import views
    2. Add a URL to urlpatterns:  path('', views.home, name='home')
Class-based views
    1. Add an import:  from other_app.views import Home
    2. Add a URL to urlpatterns:  path('', Home.as_view(), name='home')
Including another URLconf
    1. Import the include() function: from django.urls import include, path
    2. Add a URL to urlpatterns:  path('blog/', include('blog.urls'))
"""
from django.contrib import admin
from django.urls import path
from app import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('surfacearea/',views.surfacearea,name="surfacearea"),
    path('',views.surfacearea,name="areaofrectangleroot")
]

```



## SERVER SIDE PROCESSING:
![Screenshot 2024-04-16 085158](https://github.com/Jayalakshm1/MathServer/assets/130430542/305e6a71-b599-472d-a72a-f70e806d5617)

## HOMEPAGE:
![Screenshot 2024-04-16 083534](https://github.com/Jayalakshm1/MathServer/assets/130430542/f2c40bb8-bd46-418a-b782-8fee9b3e379b)

## RESULT:
The program for performing server side processing is completed successfully.
