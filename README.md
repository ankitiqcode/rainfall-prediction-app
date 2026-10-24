# 🌧️ Rainfall Prediction System 

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-blue?logo=python" alt="Python">
  <img src="https://img.shields.io/badge/Machine%20Learning-Logistic%20Regression-orange" alt="Machine Learning">
  <img src="https://img.shields.io/badge/Framework-Django-green?logo=django" alt="Django">
  <img src="https://img.shields.io/badge/Library-Scikit--learn-F7931E?logo=scikitlearn" alt="Scikit-learn">
  <img src="https://img.shields.io/badge/Status-Completed-success" alt="Project Status">
</p>

## 📌 Project Overview

The **Rainfall Prediction System** is a Machine Learning-based web application designed to predict whether it will rain based on selected weather parameters.

The project uses **Logistic Regression**, a supervised Machine Learning algorithm suitable for binary classification, to predict one of two outcomes:

- 🌧️ **Yes:** Rainfall is predicted.
- ☀️ **No:** Rainfall is not predicted.

The trained Machine Learning model is saved as `rfp.pkl` and integrated into a web application built using the Django framework. Users can enter weather information through a web interface and receive a prediction.

This project demonstrates the practical integration of Machine Learning, Python, data preprocessing, model evaluation, and web development.

## 🎯 Project Objectives

- Analyze historical weather data for rainfall prediction.
- Understand and preprocess weather-related features.
- Build a supervised Machine Learning classification model.
- Predict rainfall using temperature, precipitation, and wind speed.
- Evaluate model performance using standard classification metrics.
- Save and reuse the trained model using Pickle.
- Integrate the saved model into a Django web application.
- Provide a simple and user-friendly interface for predictions.

## 🚀 Live Demo

Try the deployed application:

**Live Application:** https://rainfall-prediction-app-4cff.onrender.com

> Note: The availability of the live application depends on the hosting service. If the application is unavailable, run the project locally using the instructions below.

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Pandas | Data manipulation and analysis |
| NumPy | Numerical computations |
| Scikit-learn | Machine Learning and model evaluation |
| Logistic Regression | Binary classification |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualization |
| Pickle | Saving and loading the trained model |
| Django | Backend web framework |
| HTML5 | Web page structure |
| CSS3 | Frontend styling |
| Git and GitHub | Version control and project hosting |
| Railway / Render | Potential application deployment platforms |

## 🧠 Machine Learning Approach

### 1. Problem Definition

The project solves a **binary classification problem**. Given weather-related input features, the model predicts a rainfall class.

The target variable represents two possible classes:

- `1` — Rain
- `0` — No Rain

The exact target encoding depends on the dataset and training code.

### 2. Input Features

The model is designed around the following weather parameters:

| Feature | Description |
|---|---|
| Maximum Temperature | Highest temperature recorded during the day |
| Minimum Temperature | Lowest temperature recorded during the day |
| Precipitation | Amount of rainfall or other measured precipitation |
| Wind Speed | Speed of the wind |

These features are used by the trained model to estimate the likelihood of the target class.

**Important:** The application must use the same feature order, units, preprocessing steps, and data transformations that were used during training.

### 3. Data Preprocessing

Data preprocessing prepares the dataset for Machine Learning.

Typical steps include:

1. Loading the dataset using Pandas.
2. Inspecting column names, data types, and statistical summaries.
3. Identifying missing or invalid values.
4. Handling missing values using an appropriate strategy.
5. Selecting relevant input features and the target variable.
6. Encoding categorical values if required.
7. Splitting the dataset into training and testing sets.
8. Standardizing numerical features if required by the training pipeline.

The exact preprocessing steps should match the implementation in the training code.

### 4. Train-Test Split

The dataset is divided into two subsets:

- **Training set:** Used to train the Machine Learning model.
- **Testing set:** Used to evaluate how well the model performs on unseen data.

A common approach is an 80:20 split, although the actual ratio depends on the implementation.

### 5. Model Selection — Logistic Regression

Logistic Regression is a supervised Machine Learning algorithm commonly used for classification problems.

It estimates the probability of a class using a logistic, or sigmoid, function:

`P(y = 1 | x) = 1 / (1 + e^(-z))`

where:

- `x` represents the input features.
- `z` is the weighted combination of the input features and model parameters.
- The output is a probability between 0 and 1.

The predicted class is determined using the decision threshold configured by the model, which is commonly 0.5.

Logistic Regression is suitable for this project because the target has two possible outcomes.

### 6. Model Evaluation

The model can be evaluated using the following metrics:

- **Accuracy:** Proportion of all predictions that are correct.
- **Precision:** Proportion of positive predictions that are correct.
- **Recall:** Proportion of actual positive cases correctly identified.
- **F1-score:** Harmonic mean of precision and recall.
- **Confusion Matrix:** Summarizes true positives, true negatives, false positives, and false negatives.

These metrics help assess the model beyond accuracy alone, particularly when the dataset has an imbalance between rainy and non-rainy days.

No specific accuracy or performance score is claimed here because the actual evaluation output has not been provided.

### 7. Saving the Trained Model

After training, the model can be serialized and saved to a file named `rfp.pkl` using Python's Pickle module.

Example:

```python
import pickle

with open("rfp.pkl", "wb") as file:
    pickle.dump(model, file)
```

The saved model can then be loaded by the Django application without retraining it for every prediction.

> **Security note:** Only load Pickle files from trusted sources. Loading an untrusted Pickle file can execute malicious code.

## 🏗️ System Architecture

The application follows this general workflow:

```text
Historical Weather Dataset
          |
          v
Data Preprocessing
          |
          v
Train-Test Split
          |
          v
Logistic Regression Training
          |
          v
Model Evaluation
          |
          v
Save Trained Model (rfp.pkl)
          |
          v
Django Web Application
          |
          v
User Enters Weather Parameters
          |
          v
Input Validation and Preprocessing
          |
          v
Load Model and Generate Prediction
          |
          v
Display Rainfall Prediction (Yes / No)
```

## 📂 Project Structure

The main Django project files are organized as follows. Some files may differ depending on the actual implementation.

```text
myproject/
│
├── manage.py
├── requirements.txt
├── db.sqlite3
│
├── myapp/
│   ├── migrations/
│   ├── templates/
│   │   └── predict.html
│   ├── static/
│   │   └── myapp/
│   │       └── style.css
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── tests.py
│   ├── urls.py
│   ├── views.py
│   └── rfp.pkl
│
└── myproject/
    ├── __init__.py
    ├── asgi.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py
```

**File descriptions:**

| File or Directory | Purpose |
|---|---|
| `manage.py` | Runs Django management commands |
| `requirements.txt` | Lists Python dependencies |
| `myapp/views.py` | Handles requests and prediction logic |
| `myapp/urls.py` | Defines application URL patterns |
| `myapp/rfp.pkl` | Stores the serialized trained model |
| `myapp/templates/` | Contains HTML templates |
| `myapp/static/` | Contains CSS and other static assets |
| `myproject/settings.py` | Contains Django project settings |
| `myproject/urls.py` | Configures project-level URL routing |
| `db.sqlite3` | Local SQLite database, if used |

The dataset and model training script may be stored separately. Their presence in the repository depends on the actual project files.

## ⚙️ Installation and Setup

### Prerequisites

Install the following before running the project:

- Python 3.x compatible with the project's dependencies
- pip
- Git (optional, for cloning the repository)
- A code editor such as Visual Studio Code

### Step 1: Clone the Repository

Replace the placeholder URL with your actual GitHub repository URL.

```bash
git clone https://github.com/ankitiqcode/rainfall-prediction-app/blob/main/README.md
```

Move into the project directory:

```bash
cd Rainfall-Prediction-System
```

### Step 2: Create a Virtual Environment

On Windows:

```powershell
python -m venv venv
```

Activate the environment:

```powershell
.\venv\Scripts\Activate.ps1
```

If you use Command Prompt instead of PowerShell:

```cmd
venv\Scripts\activate.bat
```

### Step 3: Install Dependencies

Install the packages listed in the project's requirements file:

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

If a `requirements.txt` file is missing or incomplete, add the dependencies required by the actual project, such as Django, scikit-learn, NumPy, and Pandas, using compatible versions.

### Step 4: Verify the Trained Model

Confirm that the saved model exists at:

```text
myapp/rfp.pkl
```

The model file must be present at the path expected by the prediction code.

### Step 5: Apply Database Migrations

Run:

```bash
python manage.py migrate
```

This creates or updates the database tables required by Django.

### Step 6: Start the Development Server

Run:

```bash
python manage.py runserver
```

Open the application in your browser:

http://127.0.0.1:8000/

If the application uses a different URL route, open the corresponding path defined in the Django URL configuration.

## 🖥️ How to Use the Application

1. Start the Django development server.
2. Open the application in your browser.
3. Enter the required weather parameters.
4. Submit the prediction form.
5. The application passes the input features to the trained model.
6. The predicted result is displayed on the web page.

### Example Input

The following values are illustrative examples, not validated model results.

| Input Feature | Example Value |
|---|---:|
| Maximum Temperature | 30 |
| Minimum Temperature | 20 |
| Precipitation | 5 |
| Wind Speed | 12 |

The actual units, acceptable ranges, and feature order must match the model's training data.

### Expected Output

The application displays one of the following classes:

- 🌧️ **Rainfall Predicted: Yes**
- ☀️ **Rainfall Predicted: No**

These are examples of possible output labels. The actual prediction depends on the input values and trained model.

## 🔗 How Django Integrates the ML Model

Django connects the trained Machine Learning model to the web interface.

The general integration process is:

1. Import the required Python libraries in `views.py`.
2. Load the saved model from `myapp/rfp.pkl`.
3. Receive the user's form input.
4. Validate and convert the input values to the expected numerical format.
5. Arrange the features in the exact order used during training.
6. Apply the same preprocessing used during model training.
7. Generate a prediction using the model.
8. Return the prediction to the HTML template.
9. Display the result to the user.

The model should generally be loaded once per application process rather than repeatedly for every request. Input validation and error handling should also be implemented to prevent invalid form submissions.

## 📊 Applications

Rainfall prediction can support several practical activities:

1. **Agriculture:** Helps farmers consider weather risks when planning agricultural activities.
2. **Disaster Management:** Can contribute to preliminary weather-risk assessment when combined with reliable forecasts and other data.
3. **Water Resource Management:** Supports analysis and planning related to rainfall and water availability.
4. **Tourism and Outdoor Events:** Helps users consider possible weather conditions when planning activities.
5. **Daily Planning:** Provides an additional indication of potential rainfall.

This educational model should not be treated as a replacement for official meteorological forecasts or emergency warnings.

## ⚠️ Limitations

- Prediction quality depends on the quality, quantity, and representativeness of the training dataset.
- The model only considers the features supplied to it.
- Logistic Regression may not capture complex nonlinear relationships in weather data.
- Historical patterns may not accurately represent future weather conditions.
- Missing values, inconsistent units, and incorrect feature ordering can affect predictions.
- Real-world weather forecasting requires more comprehensive observations and specialized forecasting methods.

The model's reliability should be assessed using measured test results before making claims about its predictive accuracy.

## 🔮 Future Improvements

Potential enhancements include:

- Experimenting with Random Forest, Decision Trees, Gradient Boosting, and other classifiers.
- Adding cross-validation and hyperparameter tuning.
- Improving feature engineering and handling class imbalance.
- Comparing models using precision, recall, F1-score, and ROC-AUC.
- Adding charts for historical weather data and prediction results.
- Validating user inputs and improving error messages.
- Creating automated tests for the prediction pipeline.
- Deploying the Django application to a production hosting platform.
- Adding an API endpoint for integrating predictions with other applications.
- Evaluating the model on newer, independent weather datasets.

## 🚀 Deployment

The Django application can be deployed to a platform that supports Python and Django, such as Railway or Render.

A typical deployment process includes:

1. Push the project to GitHub.
2. Configure the hosting service to access the repository.
3. Install dependencies from `requirements.txt`.
4. Configure environment variables and production settings.
5. Run database migrations.
6. Configure static file handling.
7. Start the application using a production-ready WSGI server, such as Gunicorn, where supported.
8. Test the deployed application and verify that the model file is accessible.

For production deployment, set `DEBUG = False`, configure `ALLOWED_HOSTS`, keep `SECRET_KEY` out of source control, and configure HTTPS and other security settings appropriately.

**Hosting note:** GitHub Pages serves static websites and cannot directly execute a Django backend. Use a Python-capable hosting platform for the complete application.

## 🧪 Testing and Verification

Before publishing the project, verify the following:

- The application starts without errors.
- The trained model loads from the correct path.
- The form accepts valid input and rejects invalid values.
- The feature order matches the training pipeline.
- The prediction output is displayed correctly.
- Dependencies are listed in `requirements.txt`.
- The application works in the deployed environment, if applicable.

## 🤝 Contributing

Contributions and suggestions are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Make your changes.
4. Test the updated code.
5. Submit a pull request describing the changes.

## 📄 License

No license has been specified for this project yet. Add a `LICENSE` file if you want to publish the project under an open-source license. Until a license is added, others do not automatically receive permission to reuse or redistribute your code.

## 👨‍💻 Author

**Ankit Verma**

- GitHub: https://github.com/Ankitiqcode
- Project: Rainfall Prediction System
- Technologies: Python, Machine Learning, Scikit-learn, Django, HTML, CSS

## ⭐ Support

If you find this project useful for learning Machine Learning and Django integration, consider starring the repository on GitHub.

---

*Built as a Machine Learning project to demonstrate rainfall classification and integration of a trained model into a Django web application.*


# 🌐 Live Demo

You can try the deployed Rainfall Prediction System here:

👉 Live App: https://rainfall-prediction-app-4cff.onrender.com


