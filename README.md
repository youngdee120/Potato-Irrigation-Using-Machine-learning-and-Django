# Potato-Irrigation-Using-Machine-learning-and-Django
Potato Irrigation Using Machine learning and Django

# Irrigation Management with Machine Learning and Django

A web application demonstrating how to integrate a **Machine Learning model** (Random Forest for irrigation predictions) into a **Django** web project. Users can log in, view a real-time dashboard, make predictions, and reset their passwords.

## Table of Contents

1. [Overview](#overview)  
2. [Features](#features)  
3. [Tech Stack](#tech-stack)  
4. [Setup Instructions](#setup-instructions)  
5. [Usage](#usage)  
6. [Machine Learning Workflow](#machine-learning-workflow)  
7. [Django Integration](#django-integration)  
8. [Screenshots](#screenshots)  
9. [Contributing](#contributing)  
10. [License](#license)

---

## Overview

This project showcases a simple **Irrigation Management System** that uses sensor-like inputs (temperature, soil moisture, day humidity, and night humidity) to predict whether to activate a pump (yes/no). The web front-end is built with **Django** for user authentication, dashboards, and data input, while the backend includes a **Random Forest** model for the predictions.

### Key Goals

- Demonstrate how to **train** and **save** an ML model (with scikit-learn)  
- **Scale** numerical data using a `StandardScaler` and store it for later use  
- Build a **Django** web application that allows user **signup**, **login**, **logout**, and **password reset**  
- Provide a **dashboard** with interactive **charts** (Chart.js) and a **prediction** form  

---

## Features

- **User Authentication**: Sign up, log in, log out, and password reset (via email link in the console).  
- **Dashboard**: Real-time animated charts showing temperature and soil moisture trends, plus a histogram.  
- **Prediction Form**: Users can enter new data (temperature, soil moisture, etc.) to get a pump on/off prediction.  
- **Model Training Script**: Python code that trains a Random Forest, performs hyperparameter tuning, and saves the best model to disk.  
- **Data Scaling**: Consistent feature scaling for training and inference.

---

## Tech Stack

- **Python 3.9+**  
- **Django 3+** (or 4+, depending on your version)  
- **scikit-learn** (Random Forest, StandardScaler)  
- **Bootstrap 5** for UI components  
- **Chart.js** for real-time data visualization  
- **Font Awesome** (optional) for icons  

---

## Setup Instructions

1. **Clone the Repository**  
   ```bash
   git clone https://github.com/YourUsername/irrigation-ml-django.git
   cd irrigation-ml-django

python -m venv venv
source venv/bin/activate   # macOS/Linux
# or venv\Scripts\activate  # Windows

pip install -r requirements.txt

python manage.py makemigrations
python manage.py migrate

python manage.py createsuperuser

python manage.py runserver

Open http://127.0.0.1:8000/ to view the app.

## Machine Learning Workflow
Data Preparation
The dataset includes columns like temperature, soil_moisture, day_humidity, night_humidity, and a pump label.
Scaling
We drop unneeded columns (crop_type, light_intensity), then apply a StandardScaler. The scaler is saved to models/scaler.pkl.
Model Training
A Random Forest is trained with hyperparameter tuning via GridSearchCV. The best estimator is saved to models/best_random_forest.pkl.
Inference
In the Django app, we load both scaler.pkl and best_random_forest.pkl.
New inputs are scaled with the same scaler, then passed to the model’s .predict() method.
The predicted output (0 or 1) is mapped to “yes” or “no” for the pump status.

## Django Integration
### Project Structure
myproject/
├── manage.py
├── myproject/
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
└── mainapp/
    ├── forms.py
    ├── models.py
    ├── views.py
    ├── urls.py
    ├── templates/
    └── static/


## Contributing
Fork this repo and clone it locally.
Create a branch for your feature or bugfix:

git checkout -b feature/new-idea
Commit your changes and push:

git add .
git commit -m "Add a new feature"
git push origin feature/new-idea
Open a Pull Request in GitHub describing your changes.
