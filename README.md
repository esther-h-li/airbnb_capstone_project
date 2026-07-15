# Airbnb Price Category Prediction Using Machine Learning

## Overview

This project applies machine learning techniques to predict whether an Airbnb listing in New York City is classified as **high-priced** or **low-priced** based on listing characteristics. The goal is to build a predictive model that can help identify pricing patterns and support data-driven decisions for Airbnb hosts and rental platforms.

The project follows the complete machine learning workflow:
- Data exploration and visualization
- Data preprocessing and feature engineering
- Model training and evaluation
- Neural network implementation
- Model comparison and analysis

Two supervised learning approaches were developed and compared:
1. Logistic Regression
2. Feedforward Neural Network

---

## Problem Definition

Given information about Airbnb listings, predict whether a listing belongs to the **high-price category** or **low-price category**.

This classification problem can help rental platforms identify pricing trends, evaluate potential premium listings, and assist hosts in making informed pricing decisions.

### Target Variable

`price_category`

- `0` → Low-priced listing
- `1` → High-priced listing

The original dataset categorized listings based on whether their price was above or below the 75th percentile.

---

## Dataset

The project uses the **Airbnb NYC Listings Dataset**, containing information about:
- Listing characteristics
- Location
- Room type
- Host information
- Availability
- Reviews
- Property features

Examples of features used:
- Number of guests accommodated
- Bedrooms
- Beds
- Bathrooms
- Review scores
- Availability
- Room type
- Host characteristics

---

## Data Preprocessing

The dataset required several preprocessing steps before modeling:

### Feature Selection
Removed:
- Text-based features that could not be directly modeled
- Identifier-like columns
- Irrelevant attributes

Selected predictive features including:
- `accommodates`
- `bedrooms`
- `beds`
- `bathrooms`
- `review_scores_location`
- `review_scores_cleanliness`
- `availability_60`
- `host_listings_count`
- Room type
- Host status

### Handling Missing Values
Missing numerical values were replaced using mean imputation.

### Encoding Categorical Variables
Categorical features such as room type were converted using one-hot encoding.

### Feature Scaling
StandardScaler was applied before neural network training to ensure features had comparable ranges.

### Class Imbalance
The dataset contained significantly more low-priced listings than high-priced listings. Class weighting and F1 score evaluation were used to better measure performance on the minority class.

---

## Models

## 1. Logistic Regression

A Logistic Regression classifier was trained as a baseline model.

Techniques used:
- Class weighting
- GridSearchCV hyperparameter tuning
- Coefficient analysis

### Performance

| Metric | Score |
|---|---:|
| Accuracy | 73.1% |
| F1 Score | 0.581 |

---

## 2. Neural Network

A feedforward neural network was built using TensorFlow/Keras.

### Architecture
Input Layer
|
Dense Layer (128 units, ReLU)
|
Dense Layer (64 units, ReLU)
|
Dense Layer (32 units, ReLU)
|
Output Layer (1 unit, Sigmoid)


Training configuration:
- Optimizer: SGD
- Learning Rate: 0.1
- Loss Function: Binary Crossentropy
- Epochs: 15

### Performance

| Metric | Score |
|---|---:|
| Accuracy | 81.8% |
| F1 Score | 0.588 |

---

## Model Comparison

| Metric | Logistic Regression | Neural Network |
|---|---:|---:|
| Accuracy | 73.1% | **81.8%** |
| F1 Score | 0.581 | **0.588** |

The neural network achieved higher accuracy and a slightly improved F1 score, suggesting it was able to capture more complex relationships within the Airbnb pricing data. However, the improvement in F1 score was relatively small compared to the added complexity and reduced interpretability.

---

## Key Findings

- Property characteristics such as number of guests accommodated, bedrooms, beds, and bathrooms were strongly associated with price.
- Location-based features were important predictors but introduced potential fairness concerns.
- Neural networks improved predictive performance but required more complexity and tuning.
- Class imbalance remained a challenge, particularly when identifying high-priced listings.

---

## Ethical Considerations

Machine learning models trained on pricing data may unintentionally reinforce existing socioeconomic patterns.

Potential concerns:
- Location features may act as proxies for socioeconomic characteristics.
- Historically undervalued neighborhoods could receive inaccurate predictions.
- Incorrect predictions could cause hosts to underprice or overprice their listings.

Future improvements should consider fairness-aware modeling and careful feature selection.

---

## Future Improvements

Potential improvements include:

- Additional feature engineering:
  - More detailed location features
  - Distance from landmarks
  - Neighborhood-level statistics
  - Property amenities

- Addressing class imbalance:
  - Oversampling minority classes
  - Adjusting classification thresholds
  - Using specialized imbalance techniques

- Neural network improvements:
  - Dropout layers
  - Early stopping
  - Alternative optimizers
  - Hyperparameter tuning

- Testing additional models:
  - Random Forest
  - Gradient Boosting
  - XGBoost

---

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- TensorFlow / Keras
- Matplotlib
- Seaborn
- Jupyter Notebook

---

## Project Structure


Airbnb-Price-Prediction/
│
├── data/
│ └── airbnbListingsData.csv
│
├── Airbnb_Price_Prediction.ipynb
│
├── README.md
│
└── requirements.txt


---

## Author

Esther Li

Computer Science Student  
Machine Learning & Data Science Project, originally submitted for Break Through Tech AI program
