# Uber Fare Analysis: Prediction & Causal Inference

A comprehensive machine learning project analyzing NYC Uber ride data, combining predictive modeling with causal inference techniques to understand fare pricing patterns and treatment effects.

![Project Banner](images/banner.png)

## 📊 Project Overview

This project explores Uber fare data through two complementary approaches:

1. **Fare Prediction (Regression):** Building ML models to predict trip fares based on pickup/dropoff locations, time, and passenger count
2. **Causal Inference:** Analyzing causal effects of peak hours and passenger count on fare amounts using advanced causal ML techniques

## 🎯 Key Objectives

**Part 1: Predictive Modeling**
- Predict fare amounts for NYC Uber rides
- Engineer features from geospatial and temporal data
- Compare multiple regression algorithms
- Evaluate model performance and feature importance

**Part 2: Causal Analysis**
- Estimate causal effect of peak hours on fares
- Analyze impact of passenger count on pricing
- Apply meta-learners (CausalML) and causal graphs (DoWhy)
- Validate causal assumptions through refutation tests

## 📁 Dataset

**Source:** [NYC Taxi Fare Prediction (Kaggle)](https://www.kaggle.com/competitions/new-york-city-taxi-fare-prediction)

**Size:** 200,000 rides

**Features:**
- Pickup/dropoff coordinates (latitude, longitude)
- Pickup datetime
- Passenger count
- Fare amount (target variable)

**Data Cleaning:**
- Removed outliers (fares outside $0-$100 range)
- Filtered invalid coordinates (outside NYC bounds)
- Validated passenger counts (1-6 passengers)
- Handled missing values

## 🛠️ Tech Stack

**Languages & Libraries:**
- Python (Pandas, NumPy, scikit-learn)
- Machine Learning: XGBoost, Random Forest, Linear Regression
- Causal Inference: CausalML, DoWhy
- Visualization: Matplotlib, Seaborn, SHAP

**Techniques:**
- Feature engineering (distance calculation, time features)
- Regression modeling
- Meta-learners (S-learner, T-learner)
- Propensity score matching
- SHAP values for interpretability

## 📈 Key Results

### Fare Prediction

![Model Performance](images/model_performance.png)

- Successfully predicted fares with strong performance metrics
- Distance emerged as the strongest predictor
- Time-based features captured surge pricing patterns
- Model interpretability through feature importance analysis

![Feature Importance](images/feature_importance.png)

### Causal Inference

![Causal Graph](images/causal_graph.png)

- **Peak Hour Effect:** Quantified causal impact of riding during rush hours (7-9 AM, 5-7 PM)
- **Passenger Count Effect:** Analyzed how group size affects fare amounts
- Validated findings through multiple estimation methods and refutation tests
- Identified confounders and controlled for selection bias

![Treatment Effects](images/treatment_effects.png)

## 📂 Repository Structure

```
uber-fare-analysis/
├── 01_fare_prediction/
│   └── uber_fare_prediction.ipynb
├── 02_causal_inference/
│   └── causal_inference_analysis.ipynb
├── images/
│   ├── banner.png
│   ├── model_performance.png
│   ├── feature_importance.png
│   ├── causal_graph.png
│   └── treatment_effects.png
├── requirements.txt
└── README.md
```

## 🚀 How to Run

1. Clone the repository
```bash
git clone https://github.com/MaralVahedi/uber-fare-analysis.git
cd uber-fare-analysis
```

2. Install dependencies
```bash
pip install -r requirements.txt
```

3. Download the dataset from [Kaggle](https://www.kaggle.com/competitions/new-york-city-taxi-fare-prediction) and place it in the project directory

4. Run the notebooks in order:
   - Start with `01_fare_prediction/uber_fare_prediction.ipynb`
   - Then proceed to `02_causal_inference/causal_inference_analysis.ipynb`

## 💡 Key Insights

- **Distance is king:** Trip distance is the primary driver of fare amounts
- **Peak hours matter:** Rush hour rides show measurably different pricing patterns
- **Causal vs. correlation:** Demonstrated importance of causal analysis beyond predictive modeling
- **Model interpretability:** SHAP values revealed how features contribute to predictions

## 🎓 Skills Demonstrated

- End-to-end ML pipeline development
- Feature engineering from geospatial and temporal data
- Regression modeling and evaluation
- Advanced causal inference techniques
- Statistical validation and hypothesis testing
- Data visualization and storytelling

## 📧 Contact

**Maral Vahedi**
- LinkedIn: [linkedin.com/in/maralvahedi](https://linkedin.com/in/maralvahedi)
- Email: maral.vahedi@mail.mcgill.ca

---

*This project was completed as part of coursework in the Master of Management in Analytics program at McGill University.*
