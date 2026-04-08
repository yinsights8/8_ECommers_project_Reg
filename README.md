# E-Commerce Customer Spending Prediction

A machine learning web application that predicts the **yearly spending amount** of e-commerce customers based on their engagement metrics. Built with Linear Regression and deployed via Flask.

---

## Overview

Given five customer behavior metrics, the model predicts how much a customer will spend annually. The model achieves an R² score of **0.9913** on the test set, making it highly accurate for this regression task.

---

## Project Structure

```
8_ECommers_project_Reg/
├── app.py                        # Flask web application
├── main.py                       # Entry point placeholder
├── model.pkl                     # Trained Linear Regression model
├── requirements.txt              # Python dependencies
├── Ecommerce Customers.csv       # Original raw dataset (500 records)
├── data.csv                      # Processed dataset used for training
├── Ecommers predictions.ipynb    # Full ML pipeline notebook (EDA → deployment)
├── templates/
│   ├── index.html                # Prediction input form
│   └── result.html               # Prediction result display
└── static/
    └── css/
        └── style.css             # Frontend styling
```

---

## Model Details

| Property | Value |
|---|---|
| Algorithm | Linear Regression |
| Train R² | 0.9812 |
| Test R² | 0.9913 |
| RMSE | 9.27 |
| MAE | 7.27 |
| Train/Test Split | 80/20 (random_state=898) |

### Input Features

| Feature | Type | Description |
|---|---|---|
| Avatar | Numeric (encoded) | Label-encoded avatar color (138 unique values) |
| Avg. Session Length | Float | Average minutes per session |
| Time on App | Float | Minutes spent on mobile app |
| Time on Website | Float | Minutes spent on website |
| Length of Membership | Float | Years as a customer (strongest predictor, r=0.809) |

### Target Variable

- **Yearly Amount Spent** — predicted spending in USD

---

## Setup & Installation

**Prerequisites:** Python 3.8+, [uv](https://github.com/astral-sh/uv) (or pip)

```bash
# Install dependencies
uv pip install -r requirements.txt

# Run the app
uv run app.py
```

Then open `http://localhost:8080` in your browser.

---

## How It Works

1. User visits `http://localhost:8080/` and fills in the 5 customer metrics
2. Form data is POSTed to `/predict`
3. Flask loads `model.pkl`, runs prediction, and returns the result
4. Predicted yearly spending is displayed on the results page

### API Endpoints

| Route | Method | Description |
|---|---|---|
| `/` | GET | Renders the input form |
| `/predict` | POST | Accepts form data, returns prediction |
| `/predict` | GET | Returns `{"Message": "No Predictions"}` |

---

## Dataset

- **Source:** `Ecommerce Customers.csv` — 500 customer records, 0 missing values
- **Preprocessing:** Avatar column label-encoded; non-predictive columns (Email, Address) removed
- **Processed data saved to:** `data.csv`

---

## Tech Stack

- **ML:** scikit-learn, pandas, numpy
- **Web:** Flask 3.x
- **Serialization:** Pickle
- **Frontend:** HTML5, CSS3
