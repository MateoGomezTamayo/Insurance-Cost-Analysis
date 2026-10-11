# Insurance Cost Analysis

Identifies what drives annual medical insurance charges across 2,771 records, validates the patterns with hypothesis tests, and predicts charges with three models.

**Best model:** Random Forest, **R² = 0.937**, MAE ≈ $1,494. That is about 40% less average error than the linear baseline.

## What's inside

| File | Description |
|---|---|
| `insurance_cost_analysis.ipynb` | Full analysis: cleaning, EDA, statistical tests, correlation, modeling |
| `insurance.csv` | Dataset (IBM Skills Network): age, sex, BMI, children, smoker, region, charges |
| `Informe_Analisis_Seguros.pdf` | Analysis report (Spanish) |
| `Reporte_Notebook_Seguros.pdf` | Notebook report with charts (Spanish) |

## Process

1. **Cleaning:** replace `?` placeholders, impute missing values, standardize column names.
2. **Exploratory analysis:** charge distribution, smokers vs. non-smokers, age, BMI categories, region and sex.
3. **Statistical tests:** a t-test for smokers vs. non-smokers and ANOVA across regions.
4. **Feature engineering:** an obesity flag (BMI ≥ 30) and a `smoker_obese` interaction term.
5. **Modeling:** Linear Regression, Polynomial Ridge (degree 2) and Random Forest, with residual diagnostics and feature importance.

## Results

| Model | R² | RMSE | MAE |
|---|---|---|---|
| **Random Forest** | **0.937** | **$3,211** | **$1,494** |
| Polynomial Ridge (degree 2) | 0.876 | $4,498 | $2,343 |
| Linear Regression | 0.871 | $4,587 | $2,515 |

## Key findings

- **Smoking is the main cost driver** (r = 0.79). Smokers average $32,250 per year vs. $8,418 for non-smokers, a 3.8× difference (t = 47.5, p < 10⁻²⁰⁰).
- **Obesity multiplies the effect.** Non-obese smokers fall around $15k–25k, while obese smokers jump to $30k–50k+.
- The engineered **`smoker_obese` interaction** carries over 65% of the Random Forest's predictive power. It was the single most decisive modeling choice.
- **Age** adds a steady linear baseline (r = 0.30). Sex, number of children and region have little effect (r < 0.07), although regional means do differ significantly (ANOVA F = 6.77, p = 0.0002).

## How to run

```bash
pip install -r requirements.txt
jupyter notebook insurance_cost_analysis.ipynb
```

## Tools

Python · pandas · NumPy · scikit-learn · SciPy · Matplotlib · seaborn

---
Mateo Gómez Tamayo · [LinkedIn](https://www.linkedin.com/in/mateo-g%C3%B3mez-tamayo) · [GitHub](https://github.com/MateoGomezTamayo)
