# Bayesian-ERP-Price-Prediction-using-PyMC-and-Streamlit

This project demonstrates how Bayesian regression modeling can be applied to estimate and predict the quoted price of ERP (Enterprise Resource Planning) implementation projects. Built using Python, PyMC, and Streamlit, this system uses probabilistic programming to quantify uncertainty in ERP project cost estimation — a critical factor in enterprise software planning and budgeting.

🌐 **Live Demo**: [Streamlit App](https://unmentioned-sherrill-unprovocative.ngrok-free.dev/)

---

## 🎯 Objective

To develop a robust and interpretable Bayesian regression model that predicts ERP project pricing based on multiple influencing factors including project complexity, duration, team size, client industry, and geographic region.

Unlike traditional regression, Bayesian models offer **credible intervals**, making them suitable for enterprise-level forecasting where uncertainty quantification is essential.

---

## 📊 Dataset Overview
# ERP Project Price Estimation using Bayesian and ML Modeling

This repository presents a pricing prediction framework for ERP implementation projects using structured project data. It compares Bayesian regression with traditional ML techniques like Lasso, Random Forest, and XGBoost to understand pricing drivers and estimate project costs with transparency and uncertainty quantification.

🔗 **Live App**: [Click to Open Streamlit App](https://unmentioned-sherrill-unprovocative.ngrok-free.dev/)

---

## 📌 Objective

To build interpretable and probabilistic models to predict ERP project pricing based on key project parameters, with an emphasis on:  
- Transparency of model assumptions  
- Capturing uncertainty in estimates  
- Benchmarking against classical ML methods  

---

## 📊 Dataset Overview

- **Rows:** 500 ERP projects  
- **Columns:** 8 features  

| Feature               | Type         | Description                               |
|-----------------------|--------------|-------------------------------------------|
| `Project_ID`          | Object       | Unique identifier                         |
| `Duration_Weeks`      | Float        | Project duration in weeks                 |
| `Modules_Implemented` | Integer      | Number of ERP modules implemented         |
| `Team_Size`           | Integer      | Number of team members involved            |
| `Client_Industry`     | Categorical  | Industry sector of client                  |
| `Client location`     | Categorical  | Client region (e.g., India, USA)           |
| `Complexity_Score`    | Float        | Subjective score (1–10) on project complexity |
| `Price_Quoted`        | Float        | Final quoted project price of ERP project (target)         |

✅ **No missing values**  
📈 **Target mean:** ~15,862  
📉 **Target standard deviation:** ~3,484  

---

## 🧰 Tools & Technologies

| Tool            | Purpose                                           |
|-----------------|---------------------------------------------------|
| **Python**      | Core programming language                         |
| **PyMC**        | Bayesian modeling and inference                   |
| **ArviZ**       | Posterior visualization and diagnostics           |
| **Streamlit**   | Interactive dashboard and web deployment          |
| **scikit-learn**| Data preprocessing and train-test split           |
| **Ngrok**       | Tunnel to expose local Streamlit app online       |

---

A Bayesian linear regression model was constructed using [PyMC](https://www.pymc.io/). The model estimates posterior distributions of each regression coefficient, the intercept, and the standard deviation of the residuals (`sigma`).

---

## ✅ Model Results and Interpretation

The Bayesian linear regression model provides interpretable coefficients indicating the impact of each feature on the ERP project price estimation:

| Feature                       | Coefficient (Mean in USD) | Interpretation                                 |
|------------------------------|--------------------|------------------------------------------------|
| **Intercept**                | ~181               | Base project price independent of features     |
| **Duration_Weeks**           | ~325               | Each additional week adds approximately $325  |
| **Modules_Implemented**      | ~1459              | Each additional module increases price by ~$1459 |
| **Team_Size**                | ~403               | Each extra team member adds around $403        |
| **Complexity_Score**         | ~520               | Each point increase in complexity raises price by ~$520 |
| **Region_India (dummy)**     | +43                | Projects in India priced slightly higher       |
| **Region_USA (dummy)**       | +56                | USA clients have a moderately higher quote     |
| **Client_Industry_IT_Services (dummy)** | +32   | IT services projects tend to be more expensive |

The model's noise (sigma) estimate of approximately 202 indicates relatively tight prediction intervals, suggesting consistent pricing patterns captured by the model.

These coefficients reflect expected business logic and provide a transparent view into the pricing structure across project features.

---

## 📊 Inference

- **Draws**: 2000 total (1000 warmup, 1000 posterior samples)
- **Divergences**: None
- **Convergence**: All `r_hat ≈ 1.00`
- **Posterior Diagnostics**: Clean trace plots, no pathologies
- **Output**: Posterior summaries including mean, standard deviation, and 94% HDI (Highest Density Interval)

---

## ✅ Model Results

| Feature                       | Coefficient (Mean) | Interpretation                                 |
|------------------------------|--------------------|------------------------------------------------|
| **Intercept**                | ~181               | Base price across all projects                 |
| **Duration_Weeks**           | ~325               | +325 per week of project duration              |
| **Modules_Implemented**      | ~1459              | +1459 per module added                         |
| **Team_Size**                | ~403               | +403 per team member                           |
| **Complexity_Score**         | ~520               | +520 per unit of complexity                    |
| **Region_India (dummy)**     | +43                | Slightly higher quote for India                |
| **Region_USA (dummy)**       | +56                | Even higher quote for USA clients              |
| **Client_Industry_IT_Services (dummy)** | +32   | More expensive projects in IT sector           |

> 📉 **The model's standard deviation of noise (sigma) estimate of approximately 202 indicates relatively tight prediction intervals, suggesting consistent pricing patterns captured by the model.

---

## 🧠 Model Interpretation & Summary

- 🧩 **Modules** and **project duration** are the strongest predictors of price.
- 👥 **Team size** and **complexity** have significant additive effects — consistent with real-world ERP consulting projects.
- 🌍 **Regional pricing** reflects real-world cost differences (e.g., US pricing vs India).
- 🏢 **Industry verticals** (like IT Services) slightly increase predicted cost.
- ✅ **Bayesian advantage**: We gain insight into uncertainty via full posterior distributions, not just point estimates. The model’s predictive uncertainty, captured by the posterior distribution of parameters and noise (sigma), enables construction of credible intervals, facilitating better risk assessment in pricing.

This interpretability and uncertainty quantification distinguish the Bayesian approach from traditional ML models that typically provide point estimates only.

---

## 📺 Streamlit App Features

🔗 **Launch App**: [Click here to open the app](https://unmentioned-sherrill-unprovocative.ngrok-free.dev/)

### 📌 Key Features

- 📊 **Interactive scatter plot**: Shows predicted vs actual prices with error bars
- 🎯 **Error bars**: Represent ±1 standard deviation — intuitive uncertainty interpretation
- 📋 **Posterior table**: Generated using ArviZ for statistical review
- 🧮 **Explainer**: Helps users understand where estimates come from
- 👥 **Use Case**: Perfect for ERP vendors, consulting firms, and project planners who want probabilistic pricing

---



