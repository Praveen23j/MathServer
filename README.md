# Ex.05 Design a Website for Server Side Processing
## Date:

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


<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Javascript</title>
<style>
input{
border-radius: 10px;
           padding: 10px;
           margin-top: 10px;
           margin-right:5px ;
       }
       body{
           margin-top: 15%;
       }
       h1{
           color:rgb(238, 83, 194); 
           font-size: 40pz;
           
       }
       form{
           background-color: rgb(158, 34, 34);
           width: 450px; ;
       }
   </style>
   <script>
       function pow(){
           var x=document.getElementById("a").value
           var y=document.getElementById("b").value
           document.getElementById('r').innerText="power:" +x*x*y
           
       
       }
   </script>
</head>
<body >
    <H2>
   <br>
   
   <center>
       <form >
       
       <h1>POWER CALCULATOR </h1>
    
   <input type="text" placeholder="Enter intensity" id="a">
   <br>
   <input type="text" placeholder="Enter resistance" id="b">
   <br>
   <input type="button" value="calculate" onclick="pow()"><br>
   <label id="r"></label>
</form>
   </center>
</H2>
</body>
</html>

urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('PowerOfLampFilamentInAnIncandescentBulb/',views.powerlamp,name="PowerOfLampFilamentInAnIncandescentBulb"),
    path('',views.powerlamp,name="PowerOfLampFilamentInAnIncandescentBulb")
]
views.py
from django.shortcuts import render

def powerlamp(request):
    context={}
    context['Power'] = ""
    context['I'] = ""
    context['R'] = ""
    if request.method == 'POST':
        print("POST method is used")
        I = request.POST.get('Intensity','')
        R = request.POST.get('Resistence','')
        print('request=',request)
        print('Intensity=',I)
        print('Resistence=',R)
        Power = int(I) * int(I) * int(R)
        context['Power'] = Power
        context['I'] = I
        context['R'] = R
        print('Power=',Power)
    return render(request,'mathapp/math.html',context)



## SERVER SIDE PROCESSING:
![alt text](<Screenshot 2024-12-09 081635.png>)

## HOMEPAGE:
![alt text](<Screenshot 2024-12-09 081946.png>)

## RESULT:
The program for performing server side processing is completed successfully.
