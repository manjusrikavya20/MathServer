# Ex.05 Design a Website for Server Side Processing
## Date:24/04/2025

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
math.html

<!DOCTYPE html>
<html>
<head>
    <title>Power of Lamp Filament</title>
    <style>
        body {
            font-size: 20px;
            background-color: #e6f7ff;
        }
        .formelt {
            color: #003366;
            text-align: center;
            margin-top: 20px;
        }
        h1 {
            color: #cc0000;
            text-align: center;
            padding-top: 20px;
        }
    </style>
</head>
<body>
    <div class="edge">
        <div class="box">
            <h1>Power of a Lamp Filament</h1>
            <form method="POST">
                {% csrf_token %}
                <div class="formelt">
                    Intensity (I): <input type="text" name="intensity" value="{{ i }}"> A<br><br>
                </div>
                <div class="formelt">
                    Resistance (R): <input type="text" name="resistance" value="{{ r }}"> Ω<br><br>
                </div>
                <div class="formelt">
                    <input type="submit" value="Calculate Power"><br><br>
                </div>
                <div class="formelt">
                    Power (P): <input type="text" name="power" value="{{ p }}"> watts<br>
                </div>
            </form>
        </div>
    </div>
</body>
</html>

views.py

from django.shortcuts import render

def calc_power(request):
    context = {}
    context['p'] = "0"
    context['i'] = "0"
    context['r'] = "0"

    if request.method == 'POST':
        print("POST method is used")
        i = request.POST.get('intensity')
        r = request.POST.get('resistance')
        print('Intensity =', i)
        print('Resistance =', r)

        try:
            power = float(i) ** 2 * float(r)
            context['p'] = power
        except:
            context['p'] = "Invalid input"

        context['i'] = i
        context['r'] = r
        print('Power =', context['p'])

    return render(request, 'mathapp/math.html', context)

urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('power/', views.calc_power, name='power'),  # Path for the power view
    path('', views.calc_power, name='power_root'),  # Root path to point to calc_power view
]

```

## SERVER SIDE PROCESSING:

![image](https://github.com/user-attachments/assets/672ce965-b91e-43fe-b22a-71dbaf65dde6)

## HOMEPAGE:

![image](https://github.com/user-attachments/assets/815a3ada-498d-4d42-8ce1-ac9c3268d488)


## RESULT:
The program for performing server side processing is completed successfully.
