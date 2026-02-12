# Hitter Contact Rate Projection – Rest-of-Season Modeling

Empirical Bayes (Beta–Binomial) modeling of MLB hitter rest-of-season contact rate with uncertainty quantification and shrinkage analysis.




## Problem Statement

The objective of this project is to estimate each MLB hitter’s **rest-of-season (ROS) contact rate** using only data available through June 30, 2024, while explicitly quantifying projection uncertainty.

Contact rate stabilizes more quickly than many offensive metrics, but early-season performance remains noisy—especially for hitters with limited swing volume. A robust projection system must therefore:

1. Account for **varying sample sizes**
2. Regularize noisy estimates toward a population-level prior
3. Produce calibrated **probabilistic uncertainty intervals**
4. Identify likely regression candidates (overperformers and underperformers)

---

## Technical Requirements

The modeling framework must:

- Use pitch-level data to derive hitter-level swing and contact aggregates.
- Split data into:
  - First Half (FH): through June 30, 2024
  - Rest-of-Season (ROS): after June 30, 2024
- Model contact outcomes as **Bernoulli trials**
- Apply a **Beta–Binomial Empirical Bayes framework** to:
  - Stabilize small-sample hitters via shrinkage
  - Estimate posterior mean contact probability
  - Compute 80% credible intervals
- Evaluate model performance using:
  - Mean Absolute Error (MAE)
  - Root Mean Squared Error (RMSE)
  - Interval coverage calibration
- Analyze projection performance across swing-volume bins
- Identify:
  - Underperformers (true skill > observed FH performance)
  - Overperformers (FH performance > projected skill)

---

## Modeling Approach

The final model uses an **Empirical Bayes Beta–Binomial stabilizer**, selected after comparison with:

- Weighted Logistic Regression (GLM)
- Hierarchical Bayesian Logistic Regression

The Empirical Bayes model was chosen for its:

- Statistical interpretability
- Computational efficiency
- Natural variance reduction via sample-size-based shrinkage
- Competitive predictive accuracy

Posterior estimates provide both point projections and credible intervals for ROS contact rate.

---

## Deliverables

- `contact_projection.ipynb`  
  Full modeling workflow, feature engineering, posterior estimation, validation, and evaluation.

- `Report.pdf`  
  Structured analysis detailing methodology, evaluation results, calibration behavior, and decision-making implications.

---

## Key Insight

Projection accuracy is strongly driven by first-half swing volume.  
Shrinkage toward the league prior reduces volatility for small samples while allowing large-sample hitters to reflect individual skill.

The framework provides a principled probabilistic approach for identifying regression candidates and supporting decision-making under uncertainty.
