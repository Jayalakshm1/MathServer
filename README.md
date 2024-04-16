# Ex.05 Design a Website for Server Side Processing
## Date:

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
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
<style>
.formelt{
    color: orange;
    text-align: center;
    margin-top: 7px;
    margin-bottom: 6px;
}
h1 {
    color: rgb(255, 0, 179);
    text-align: center;
    padding-top: 20px;
}
body{
    background-color:palegreen;
}
.edge
{
    border:2px solid wheat;
    margin-top:10%;
}
</style>
</head>
<body>
    <h1>Area of a Rectangle</h1>
<div class="edge">
    <div class="box">
        <form method="POST">
            {% csrf_token %}
            <div class="formelt">
                Length: <input type="text" name="length" value="{{l}}"></input>(in m)<br/>
            </div>
            <div class="formelt">
                Breadth <input type="text" name="breadth" value="{{b}}"></input>(in m)<br/>
            </div>
            <div class="formelt">
                <input type="submit" value="Calculate"></input><br/>
            </div>
            <div class="formelt">
                Area: <input type="text" name="area" value="{{area}}"></input>m<sup>2</sup><br/>
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

# Create your views here.from django.shortcuts import render
def rectarea(request):
    context={}
    context ['area'] = "0"
    context['1'] = "0"
    context ['b'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        l=request.POST.get('length', '0')
        b = request.POST.get('breadth', '0')
        print('request=', request)
        print('Length=',l)
        print('Breadth=',b)
        area = int(l)*int(b)
        context['area'] = area
        context['l']= l
        context['b'] = b
        print('Area', area)
    return render(request, 'app/math.html', context)
```
## urls.py
```
from django.contrib import admin
from django.urls import path
from app import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaofrectangle/',views.rectarea,name="areaofrectangle"),
    path('',views.rectarea,name="areaofrectangleroot")
]
```



## SERVER SIDE PROCESSING:
![image](https://github.com/Jayalakshm1/MathServer/assets/130430542/277aca83-ea29-4359-8917-362037478ea6)


## HOMEPAGE:
![image](https://github.com/Jayalakshm1/MathServer/assets/130430542/45c8e0cc-b558-46ae-a58d-a06a1b7148cc)


## RESULT:
The program for performing server side processing is completed successfully.
