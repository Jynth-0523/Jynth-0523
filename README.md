# Jingshi Xu

I study economics and statistical science, with interests in empirical asset pricing,
statistical learning, optimization, and reproducible research. I use coursework and
projects to connect mathematical methods with working software.

[Factor Discovery website](https://jynth-0523.github.io/) ·
[Platform source and example CSV](https://github.com/Jynth-0523/Jynth-0523.github.io#try-it-with-a-ready-to-use-csv)

The sections below cover methods I have studied through coursework and used in
research or software projects. I distinguish course foundations from applied work;
my projects combine library implementations, custom numerical routines, and adapted
open-source components where appropriate.

[Computer science](#computer-science-algorithms-and-systems) ·
[Statistical learning and optimization](#statistical-learning-and-optimization) ·
[Projects](#selected-projects)

## Computer science algorithms and systems

### Sorting, searching, and data structures

- **Insertion sort, bubble sort, optimized bubble sort, and selection sort:**
  comparison-based sorting studied through C++ course examples, including
  early termination and shrinking the unsorted boundary.
- **Binary search:** locating an element in a sorted array in coursework;
  finding a monotone price/inventory threshold in the Kaggriculture project.
- **Array traversal and matrix algorithms:** indexed scans, elementwise addition,
  and the three-loop matrix-multiplication algorithm in C++.
- **Hash maps and hash sets:** keyed lookup, grouping, duplicate detection,
  visited-state tracking, and reuse of computed results through standard containers.
- **Composite-key indexing:** detecting duplicate entity-date observations and
  mapping entity identifiers across adjacent periods.
- **Bitmask state representation:** encoding visited task subsets, testing
  membership, adding tasks, and enumerating complementary assignments.
- **Sort-and-scan ranking:** sorting observations, grouping equal values, and
  assigning average ranks to ties; explicit tie-breakers for planning candidates.

### Combinatorial search and dynamic programming

The [Kaggriculture project code](https://github.com/Jynth-0523/Kaggriculture/blob/main/main.py)
contains several complementary planning techniques:

- **Beam search:** expanding candidate action sequences and retaining a bounded
  set of promising states under movement, time, and resource constraints.
- **Subset dynamic programming:** storing the best route for a visited-task mask
  and ending location, then extending it with feasible unvisited jobs.
- **Dominance pruning:** retaining the shorter route for equivalent visited-set
  and endpoint states when the model's resource and deadline assumptions permit it.
- **Two-worker task partitioning:** combining complementary subsets and comparing
  assignments by maximum completion time, then total work.
- **Feasibility and lower-bound pruning:** rejecting states that exceed action
  budgets or carried resources, including Manhattan-distance bounds for return trips.
- **Bounded subset enumeration:** reconsidering small combinations of valuable
  jobs beyond the initial greedy ordering.
- **Greedy scoring and deterministic tie-breaking:** ranking action alternatives
  by value, cost, timing, and consistent secondary criteria.
- **Simulation-based local plan repair:** removing redundant commands or replacing
  short schedules only after comparing their resulting state and resource balances.
- **Memoization:** caching repeated schedule, transition, and market evaluations
  within the appropriate state context.

Earlier local planning experiments also explored **top-down recursive dynamic
programming with memoization** for finite-horizon planting choices. That experimental
planner is distinct from the published agent. The project integrates credited
upstream code and route data; these methods are not a claim of training an online
neural reinforcement-learning policy.

### Streaming, parsing, and data-processing algorithms

Applied in the [Factor Discovery browser worker](https://github.com/Jynth-0523/Jynth-0523.github.io/blob/main/web/app/factor-discovery.worker.ts):

- **State-machine CSV parsing:** tracking quoted fields and escaped quotes while
  preserving parsing state across input chunks.
- **Incremental UTF-8 decoding and streaming scans:** processing file chunks,
  retaining selected columns, and enforcing row and memory limits.
- **Hash-based grouping and joins:** constructing period buckets and identifier
  lookup tables without relying on row order to match entities.
- **Indexed temporal traversal:** following aligned entity positions to compute
  lags, changes, rolling means, and rolling volatility.
- **Map/filter/reduce pipelines:** transforming observations, excluding invalid
  values, aggregating results, and maintaining index alignment.
- **Bounded combinatorial formula generation:** enumerating allowed unary and
  pairwise operations, limiting search size, and deduplicating equivalent proposals.
- **Structural and semantic validation:** checking operation allowlists, operand
  arity, feature references, and typed proposal fields before evaluation.

### Graph traversal, hashing, and integrity checks

Applied in the platform's [runtime store](https://github.com/Jynth-0523/Jynth-0523.github.io/blob/main/backend/src/research_platform/store.py)
and [integrity utilities](https://github.com/Jynth-0523/Jynth-0523.github.io/blob/main/backend/src/research_platform/util.py):

- **Parent-link traversal with a visited set:** checking an audit chain for cycles,
  missing parents, and records unreachable from its head.
- **Canonical serialization:** sorting JSON keys and fixing encoding and separators
  before computing content digests.
- **SHA-256 hashing:** using standard-library implementations for file and artifact
  integrity, including chunked hashing of larger files.
- **Hash-linked audit records:** connecting successive result records and verifying
  both their contents and predecessor references.
- **Deterministic source-tree fingerprinting:** sorting relative file paths and
  hashing length-delimited paths and contents.

### Concurrency, persistence, and software construction

These are systems techniques used alongside algorithms:

- **Mutual exclusion:** nonblocking file locks for single-instance execution.
- **Idempotent job claims:** exclusive creation, completion markers, and lease-based
  stale-claim recovery within the platform's locking model.
- **Atomic file publication:** temporary-file writes, flush/synchronization, atomic
  replacement, and exclusive publication for records that must not be overwritten.
- **Worker message passing and cooperative cancellation:** browser computation
  separated from the interface, with progress messages and active-job checks.
- **State-scoped caching and copy isolation:** invalidating cached evaluations when
  observations change and copying mutable results before downstream use.
- **Relational integrity and indexed retrieval:** PostgreSQL primary/composite keys,
  secondary indexes, and bulk loading for research records.
- **Finite-state workflows:** explicit review states, version-bound decisions,
  rule checks, and human approval in research workflow software.
- **C++ object and memory management:** dynamic two-dimensional arrays, constructors,
  destructors, deep-copy construction, copy assignment, bounds checks, and operator
  overloading in the matrix coursework.

## Statistical learning and optimization

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
| [Kaggriculture](https://github.com/Jynth-0523/Kaggriculture) | Python strategy integration, beam search, subset dynamic programming, constrained scheduling, and reproducible local comparisons |
| [Paper Reproduction using R](https://github.com/Jynth-0523/Paper-Reproduction-using-R) | Selected tables and figures from *The Rate of Return on Everything* |
| [Economic Policy Uncertainty and Stock Return Volatility](https://github.com/Jynth-0523/The-Impact-of-EPU-on-Firm-Level-Stock-Return-Volatility_Evidence-from-U.S.-Firms) | Firm fixed-effects regressions, clustered inference, and specification checks |
| [Research and Wealth Assistant Demo](https://github.com/Jynth-0523/kingstar-ai-demo) | Rule-based context checks, evidence review, and human approval workflows using synthetic examples |

## Tools

Python · R · Julia · C++ · JavaScript/TypeScript · SQL · PostgreSQL · MySQL · Tableau

I keep data timing, model selection, and out-of-sample evaluation separate.
Course exercises, synthetic demonstrations, software tests, and empirical research
results answer different questions; performance claims belong with the relevant
project's evidence and limitations.
