# Design a Website for Server Side Processing

# AIM:

To design a website to perform mathematical calculations in server side.

# DESIGN STEPS:

## Step 1:
Design  your website for calculation using wireframe work.

## Step 2:
Then to execute the wireframe work desing use html,css.


## Step 3:
Use views.py to execute the coding in serverside.

## Step 4:
Mention the path of the website in urls.py


## Step 5:

Publish the website in the given URL.

# PROGRAM:
*HTML CODE

<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>Volume Calculator</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    
</head>
<style>
    *{
        box-sizing: border-box;
        font-family: Arial, Helvetica, sans-serif;
    }

    body{
    background-color: lightblue;
    color:blue;
    }

    .container{
    width: 1080px;
    height: 350px;
    margin-top: 100px;
    margin-left: auto;
    margin-right: auto;
    border-radius: 25px;
    border: 10px solid cyan;
    box-shadow: inset 0 0 15px rgb(231, 217, 160);
    background-color:lightgreen;
    }
    h1{
        color: rgb(0, 0, 0);
        text-align: center;
    }
    .calculate{
        padding-top: 10px;
        padding-bottom: 10px;
        padding-left: 10px;
        padding-right:10px;
        text-align: center;
        font-size: 20px;
        padding-top: 7px;
        font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
    }
</style>
<body>
    <div class="container">
        <h1>VOLUME OF OF A CUBOID</h1>
        <h3 align="centre">G PAVANA (22008660)</h3>
        <form method="POST">
            {% csrf_token %}
            <div class="calculate"> 
                Enter Height:<input type="text" name="height" value={{h}}></input><br/>
            </div>
            <div class="calculate">
                Enter Length:<input type="text" name="length" value={{l}}></input><br/>
            </div>
            <div class="calculate">
                Enter Width:<input type="text" name="width" value={{w}}></input><br/>
            </div>
            <div class="calculate">
                <input type="submit" value="Calculate Volume"></input><br/>
            </div>
            <div class="calculate">
                Volume:<input type="text" name="volume" value={{volume}}></input>
            </div>
        </form>
    </div>
</body>
</html>

Views.py

from django.shortcuts import render

def volumecalculation(request):
    context ={}
    context["volume"]='0'
    context["h"]='0'
    context["l"]='0'
    context["w"]='0'
    if request.method == 'POST':
        
        h=request.POST.get('height','0')
        l=request.POST.get('length','0')
        w=request.POST.get('width','0')
        volume=int(h)*int(l)*int(w)
        context['volume'] = volume
        context['l']=l
        context['h']=h
        context['w']=w
    return render(request,"myapp/math.html",context)

urls.py

from django.contrib import admin
from django.urls import path
from myapp import views

urlpatterns=[
    path('admin/',admin.site.urls),
    path('volofrectangulartank/',views.volumecalculation,name="volofrectangulartank"),
    path('',views.volumecalculation,name="volofrectangulartankroot")
]

# OUTPUT:

![OUTPUT](./out.png)
# RESULT:

A website to perform mathematical calculations in server side is created.
