# Jingshi Xu

I study economics and statistical science, with interests in empirical asset pricing,
statistical learning, optimization, and reproducible research. I use coursework and
projects to connect mathematical methods with working software.

[Factor Discovery website](https://jynth-0523.github.io/) ·
[Platform source and example CSV](https://github.com/Jynth-0523/Jynth-0523.github.io#try-it-with-a-ready-to-use-csv)

## Algorithms and methods

The sections below cover methods I have studied through coursework and used in
research or software projects. I distinguish course foundations from applied work;
my projects combine library implementations, custom numerical routines, and adapted
open-source components where appropriate.

### Regression and predictive modeling

Methods used in statistical coursework and independent research:

- Ordinary least squares (OLS), multiple linear regression, and weighted least
  squares (WLS).
- Forward stepwise selection with WLS and backward selection using AIC.
- Ridge regression, Lasso, and Elastic Net regularization.
- Group Lasso and two-stage Adaptive Group Lasso with grouped cubic B-spline bases.
- Principal component regression (PCR).
- Ordinal logistic regression, including proportional-odds and partial
  proportional-odds models.
- Random forests and gradient-boosted regression trees.
- Fixed-effects panel regression, interaction specifications, and lagged-predictor
  models for empirical economic research.

Applications include equity-return prediction, comparisons of point-in-time and
revised accounting data, ordinal wine-quality prediction, and firm-level volatility
analysis. The forecasting models in my paper research are separate from the
browser-based factor-discovery platform.

### Multivariate analysis and statistical learning

Coursework topics include principal component analysis (PCA), factor analysis,
clustering, dimensionality reduction, matrix completion, and high-dimensional data
analysis. My applied work also uses rank transformations, standardization,
correlation-based redundancy reduction, and permutation feature importance.

### Statistical inference and model evaluation

- Likelihood-based estimation and maximum likelihood estimation (MLE), with
  Bayesian inference and Monte Carlo simulation studied in statistical coursework.
- Bootstrap resampling, including grouped/profile-level bootstrap and percentile
  confidence intervals in the wine-quality project.
- Hypothesis testing, Newey-West heteroskedasticity and autocorrelation consistent
  (HAC) inference, and firm-clustered standard errors.
- Holm-Bonferroni adjustment for explicitly defined multiple-testing families.
- K-fold cross-validation, leave-one-out cross-validation (LOOCV), grouped and
  stratified validation, and training-fold-only preprocessing and model selection.
- Time-ordered validation, expanding and rolling training windows, purging around
  forward-return horizons, and walk-forward out-of-sample evaluation.
- AIC/BIC model comparison and hyperparameter grid search.
- Regression and probabilistic-prediction evaluation using MSE/RMSE, MAE, log loss,
  and ranked probability score (RPS).

### Numerical optimization and linear algebra

Methods used in the research implementations include:

- Coordinate-descent regularization paths for Elastic Net.
- Accelerated proximal-gradient optimization with restart and group
  soft-thresholding for Adaptive Group Lasso.
- Karush-Kuhn-Tucker (KKT) residual checks and convergence diagnostics.
- Cubic B-spline expansion, weighted quantiles, group centering, and
  eigendecomposition-based whitening.
- Matrix operations, weighted quadratic objectives, and numerical linear-system
  calculations.

### Mathematical optimization and graph models

Studied through engineering-optimization coursework and exercises:

- Linear programming (LP), integer linear programming (ILP), and binary-variable
  formulations.
- The simplex method, basis updates, reduced costs, ratio tests, and Phase I/Phase II.
- Primal-dual formulations, weak and strong duality, complementary slackness, and
  optimality certificates.
- Sensitivity analysis for resource bounds, objective coefficients, and new variables.
- Shortest-path edge-selection and label formulations; network-flow conservation.
- Minimum vertex cover, LP relaxation, edge-packing duals, and conflict-based scheduling.
- Transportation and resource-allocation models.
- Linear reformulations of max-min objectives and absolute-deviation minimization.

These entries describe optimization methods and modeling topics, rather than a
claim to have implemented every specialized graph solver from scratch.

### Dynamic programming and decision-making

In computational economics coursework, I worked with dynamic programming, Bellman
equations, stochastic optimization, and simulation of heterogeneous-agent economies.
Applications involved asset accumulation, income shocks, and risk-sharing constraints
using Julia.

Related theoretical study includes Nash and subgame-perfect equilibrium, Bayesian
and repeated games, bargaining, and incentive compatibility. These are foundations
for decision models, not additional software algorithms.

### Core programming algorithms

C++ coursework covered insertion sort, bubble sort and an early-exit/shrinking-bound
variant, selection sort, binary search, array traversal, and matrix addition and
multiplication. I also practiced dynamic memory management and object-oriented
matrix implementations.

### Search and planning in projects

- **Factor discovery:** bounded formula enumeration, lag/change/rolling operators,
  nonlinear and interaction transformations, rank-based screening with Spearman
  RankIC, redundancy control, and frozen ensemble evaluation.
- **Kaggriculture:** heuristic action selection, production and logistics scheduling,
  constrained resource allocation, opponent-aware scenario evaluation, and
  reconciliation of predicted actions with observed inventory. The published agent
  builds on credited upstream code and route data; it is not an online neural
  reinforcement-learning system.
- **Research workflow software:** rule-based information checks, finite-state
  approval workflows, version-bound decisions, and deterministic evidence checks.

## Selected projects

| Project | Focus |
| --- | --- |
| [Factor Discovery Research Platform](https://github.com/Jynth-0523/Jynth-0523.github.io) | Browser-based factor discovery and validation, Python research operations, PostgreSQL records, and Tableau reporting |
| [Kaggriculture](https://github.com/Jynth-0523/Kaggriculture) | Python strategy integration, constrained planning, and reproducible local comparisons |
| [Paper Reproduction using R](https://github.com/Jynth-0523/Paper-Reproduction-using-R) | Selected tables and figures from *The Rate of Return on Everything* |
| [Economic Policy Uncertainty and Stock Return Volatility](https://github.com/Jynth-0523/The-Impact-of-EPU-on-Firm-Level-Stock-Return-Volatility_Evidence-from-U.S.-Firms) | Firm fixed-effects regressions, clustered inference, and specification checks |
| [Research and Wealth Assistant Demo](https://github.com/Jynth-0523/kingstar-ai-demo) | Rule-based context checks, evidence review, and human approval workflows using synthetic examples |

## Tools

Python · R · Julia · C++ · JavaScript/TypeScript · SQL · PostgreSQL · MySQL · Tableau

I keep data timing, model selection, and out-of-sample evaluation separate.
Course exercises, synthetic demonstrations, software tests, and empirical research
results answer different questions; performance claims belong with the relevant
project's evidence and limitations.
