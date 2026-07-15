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
