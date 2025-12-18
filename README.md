# Ex.04 Design a Website for Server Side Processing
## Date:
17/12/2025

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
views.py
from django.shortcuts import render

# Create your views here.
def bmi_calculator(request):
    bmi = None
    category = None

    if request.method == "POST":
        weight = float(request.POST.get("weight"))
        height = float(request.POST.get("height"))

        # Convert height from cm to meters
        height_m = height / 100

        # BMI formula
        bmi = weight / (height_m ** 2)
        bmi = round(bmi, 2)

        # Classification
        if bmi < 18.5:
            category = "Underweight"
        elif 18.5 <= bmi < 24.9:
            category = "Normal weight"
        elif 25 <= bmi < 29.9:
            category = "Overweight"
        else:
            category = "Obesity"

    return render(request, "bmicalculator.html", {
        "bmi": bmi,
        "category": category
    })

    bmicalculator.html
    <!DOCTYPE html>
<html>
<head>
    <title>BMI Calculator</title>
    <style>
        body { font-family: Arial; padding: 20px; }
        form {
            width: 300px;
            padding: 20px;
            border: 1px solid #888;
            border-radius: 8px;
            margin-left: 50%;
            transform: translateX(-50%);
        }
        input { width: 100%; margin: 10px 0; padding: 8px; }
        .result { margin-top: 20px; padding: 10px; background: #f1f1f1; }
    </style>
</head>

<body>
    <h2 align="center">BMI Calculator (Server-side in Django)</h2>

    <form method="POST">
        {% csrf_token %}
        <label>Weight (kg)</label>
        <input type="number" step="0.1" name="weight" required>

        <label>Height (cm)</label>
        <input type="number" step="0.1" name="height" required>

        <button type="submit">Calculate BMI</button>
        {% if bmi %}
        <div class="result">
            <strong>Your BMI:</strong> {{ bmi }}<br>
            <strong>Category:</strong> {{ category }}
        </div>
        {% endif %}
    </form>

    
</body>
</html>

```

## SERVER SIDE PROCESSING:
![alt text](<Screenshot 2025-12-18 090450-1.png>)



## HOMEPAGE:
![alt text](<Screenshot 2025-12-18 090434-1.png>)


## RESULT:
The program for performing server side processing is completed successfully.
