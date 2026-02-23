# Uber Fare Analysis: From Prediction to Causality

This project tells a two-part data science story on NYC Uber fares:

1. **Can we predict fares accurately?**  
2. **What actually causes fares to change?**

I answer these with two connected notebooks: one predictive, one causal.

---

## Project Story

### Why this project
Raw fare differences can be misleading. A ride during peak hour may look more expensive simply because it is longer or in a different area.  
So I split the work into:
- **Notebook 1:** build a strong predictive baseline
- **Notebook 2:** estimate causal treatment effects after controlling confounders

### Notebook map

| Notebook | Core Question | Main Methods | Output |
|---|---|---|---|
| `01_fare_prediction/uber_fare_prediction.ipynb` | How well can fare be predicted? | EDA, feature engineering, regression models, tuning, residual diagnostics | Best predictive model + error profile |
| `02_causal_inference/causal_inference_analysis.ipynb` | Which factors causally shift fares? | CausalML (S/T/X learners), DoWhy backdoor estimators, refutation checks | Causal effect estimates for two treatments |

---

## Act I: Predictive Modeling (Notebook 1)

I start with data cleaning and geospatial/temporal feature engineering, then compare multiple regressors before selecting a final model.

### Model comparison (RMSE)

| Model | RMSE | Status |
|---|---:|---|
| Linear Regression | 3.45 | Baseline |
| Random Forest | 2.85 | Default |
| **Random Forest** | **2.78** | **Tuned (selected)** |
| Gradient Boosting | 2.92 | Default |
| Gradient Boosting | 3.66 | Tuned |

The tuned Random Forest was selected for final evaluation due to lowest error and stable behavior.

![Predictions vs Actual](images/predictions_vs_actual.png)

### Final held-out test performance

| Metric | Value |
|---|---:|
| RMSE | 3.718 |
| MAE | 2.014 |
| R^2 | 0.828 |

Residual diagnostics show low systematic bias and expected spread at higher fares.

![Residual Analysis](images/residual_analysis.png)

---

## Act II: Causal Inference (Notebook 2)

After prediction, I move to causal questions using the cleaned dataset (`194,063` rides).

### Treatments studied

| Treatment | Definition | Why it matters |
|---|---|---|
| Peak hour | 7-9 AM or 5-7 PM | Potential surge/traffic effect |
| High passenger count | `passenger_count >= 3` | Possible vehicle/trip-type effect |

![Peak Hour Treatment Distribution](images/peak_hour_treatment_distribution.png)

### Causal results summary

| Treatment | CausalML | DoWhy | Practical read |
|---|---|---|---|
| Peak hour | ~0.15 to 0.16 | ~0.15 to 0.16 (core methods) | Stronger of the two effects |
| High passenger count | LRS: 0.121, XGB: 0.132 | Avg: 0.118 (range: 0.090 to 0.154) | Small positive effect |

![CausalML Effect Distributions](images/causalml_effect_distributions.png)

### Main causal takeaway
- Both treatments have **positive** estimated causal effects.
- **Peak hour** has a larger effect than passenger count.
- **Distance** remains the dominant fare driver across both predictive and causal views.

---

## Data

Source: [NYC Taxi Fare Prediction (Kaggle)](https://www.kaggle.com/competitions/new-york-city-taxi-fare-prediction)

Place these in project root:
- `uber.csv.zip` (or extracted `uber.csv`) for Notebook 1
- `uber_cleaned.csv` for Notebook 2 (created by Notebook 1 workflow)

---

## Reproducibility

```bash
git clone https://github.com/MaralVahedi/uber-fare-analysis.git
cd uber-fare-analysis
python -m pip install -r requirements.txt
```

Run notebooks in order:
1. `01_fare_prediction/uber_fare_prediction.ipynb`
2. `02_causal_inference/causal_inference_analysis.ipynb`

---

## Skills Demonstrated

| Area | Demonstrated Through |
|---|---|
| Data quality + EDA | Outlier rules, missingness handling, distribution analysis |
| Feature engineering | Distance, temporal, and contextual features |
| Predictive ML | Model selection, tuning, residual/error diagnostics |
| Causal inference | Meta-learners + backdoor estimators + robustness checks |
| Communication | Framing results as prediction vs causation |

---

## Contact

Maral Vahedi  
- LinkedIn: [linkedin.com/in/maralvahedi](https://linkedin.com/in/maralvahedi)  
- Email: maral.vahedi@mail.mcgill.ca
