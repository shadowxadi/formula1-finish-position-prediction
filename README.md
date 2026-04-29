# 🏎️ Formula 1 Finish Position Prediction

## Overview

This project predicts Formula 1 race finishing positions using historical race data and machine learning models.

The solution uses feature engineering, gradient boosting models, and ensemble learning to improve prediction accuracy.

---

## Problem Statement

The goal is to predict the finishing position of each driver in a race using historical Formula 1 race data.

Each race contains multiple drivers competing simultaneously, making this a race-level prediction problem.

---

## Dataset Features

The dataset includes:

- Driver ID  
- Constructor ID  
- Grid Position  
- Qualifying Times  
- Rolling Performance Statistics  
- Race Information  
- Finishing Positions (Target)

---

## Feature Engineering

Feature engineering played the most important role in improving model accuracy.

### Qualifying Features

- Qualifying gap to fastest driver  
- Grid rank  
- Qualifying rank  
- Grid advantage  

Example features:

- `qual_gap`
- `grid_rank`
- `qual_rank`

---

### Driver Performance Features

Rolling averages were used to track driver performance over recent races.

Example features:

- Driver last 3-race average  
- Driver last 5-race average  
- Momentum difference  

Example variables:

- `driver_form_3`
- `driver_form_5`
- `momentum_delta`

---

### Historical Strength Features

Long-term driver and constructor ability was modeled using expanding averages.

Example features:

- `driver_skill`
- `constructor_strength`
- `driver_constructor_combo`

---

### Race-Level Features

These features measure competition strength within each race.

Example features:

- `race_size`
- `grid_relative`
- `driver_vs_field`
- `constructor_vs_field`

---

## Models Used

### LightGBM

Used for fast gradient boosting with strong performance on tabular data.

Key parameters:

- Objective: MAE  
- Learning rate: 0.015  
- Num leaves: 80  
- Feature fraction: 0.8  
- Bagging fraction: 0.8  

---

### CatBoost

Two CatBoost models were trained:

- Depth 6  
- Depth 8  

CatBoost improved performance by modeling complex relationships.

---

## Model Ensemble

Final predictions were generated using weighted averaging of:

- LightGBM  
- CatBoost Depth 6  
- CatBoost Depth 8  

Weighted blending improved prediction stability and accuracy.

---

## Validation Strategy

Time-based validation was used:

Training Data:

year ≤ 2018

Validation Data:

year > 2018

Evaluation Metric:

Mean Absolute Error (MAE)

---

## Post-processing

Predictions were:

1. Rounded  
2. Clipped between 1 and 20  
3. Ranked within each race  

This ensured valid race finishing positions.

---

## Technologies Used

- Python  
- Pandas  
- NumPy  
- LightGBM  
- CatBoost  
- Scikit-learn  

---

## Skills Demonstrated

- Machine Learning  
- Feature Engineering  
- Ensemble Modeling  
- Time-Series Validation  
- Data Processing  
- Model Optimization  

---

## Author

Aditya Pratap
Anushka Goyal
Machine Learning Enthusiast
