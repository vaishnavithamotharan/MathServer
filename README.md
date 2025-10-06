# Ex.05 Design a Website for Server Side Processing
## Date:30.09.2025

## AIM:
 To design a website to calculate the Body Mass Index (BMI) in the server side. 


## FORMULA:
P = W/H<sup>2</sup>
<br> BMI -->Body Mass Index
<br> W --> Weight
<br> H --> Height

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
math.html

<html>
    <head>
        <title>BMI Calculator</title>
        <style>
        body{
          background-color: rgba(12, 243, 243, 0.745);
          border-top: 10;
        }
        .m{
          background-color: rgb(91, 99, 245);
          border-style: inset;
          margin-top: 150px;
          margin-left: 200px;
          margin-right: 200px;
          
        }
        *{
          color: rgb(130, 108, 237);
        }
            .main{
                font-size: 250%;
                text-align: center;
                text-decoration:underline;

                background-color: rgba(27, 165, 229, 0.779);
                 margin-left: 50px;
                  margin-right: 50px;
                  padding: 50px;
                  
                  
            }
            .a{
                font-size: 150%;
                text-align: center;
                background-color: rgba(103, 217, 237, 0.779);
                 margin-left: 50px;
                  margin-right: 50px;
                
                 
            }
            form{
              text-align: center;
              background-color: rgba(218, 215, 228, 0.779);
               margin-left: 50px;
             margin-right: 50px;
             padding: 50px;
            }
           
        </style>
    </head>
    <body>

       <div class="m">
        <div class="main" style="color: rgb(24, 20, 229);">BMI Calculator</div>
        <div class="a">
      <h2>VAISHNAVI T-25017435</h2></div>
        <form method="post">
          {% csrf_token %}
           
           
            <label>Weight(kg)=</label>
            <input type="text" name="weight" value="{{w}}"><br><br>
             <label>Height(cm)=</label>
            <input type="text" name="height" value="{{h}}"><br><br>
            <button type="submit">Calculate</button><br><br>
            <label>BMI=</label>
            <input type="text" name="bmi" value="{{bmi}}">
        </div>
         </form>
        
        
    </body>
</html>

 views.py

 from django.shortcuts import render
def calculate_bmi(request):
    context={}
    context['bmi']="0"
    context['w']="0"
    context['h']="0"
    if(request.method=='POST'):
       w= float(request.POST.get('weight','0'))
       h=float(request.POST.get('height','0'))
       print('request=',request)
       
       print('Weight=',w)
       print('Height=',h)
       bmi=w/((h/100)**2)
       context['bmi']=bmi
       context['w']=w
       context['h']=h
       print('BMI=',bmi)
    return render(request,'myapp/math.html',context)

    urls.py

    from django.contrib import admin
from django.urls import path
from myapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('bmi/',views.calculate_bmi,name="bmi"),
    path('',views.calculate_bmi,name="bmicalculator")
]

```


## SERVER SIDE PROCESSING:
![alt text](<Screenshot (39).png>)

## HOMEPAGE:
![alt text](<Screenshot (38).png>)

## RESULT:
The program for performing server side processing is completed successfully.
