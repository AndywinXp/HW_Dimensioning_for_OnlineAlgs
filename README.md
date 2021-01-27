# Constrained Hardware Dimensioning for Online Algorithms under Uncertainty
Experimental evaluation.

We propose an approach for automatic hardware dimensioning of these algorithms under an heterogeneous set of constraints: this is a first attempt in the direction of matching available computing resources and algorithm configuration. 
We rely on the integration of Machine Learning models within an optimization problem, following the Empirical Model Learning paradigm by Lombardi et al, "Empirical decision model learning", 2017. Machine Learning is used for benchmarking the target algorithm on different hardware configurations and optimization is used to find the optimal matching of computing resources and algorithm configuration, while respecting user-defined constraints (e.g., cost, time, solution quality). The empirical evaluation shows that our method can find optimal configurations for new, unseen data instances, while its flexibility allows the adoption of different constraints and/or objectives, as required by users.

## Approach Detail

We propose an optimization method composed of an optimization model and three ML regression models, each one devoted to predicting a specific target, given a certain number of traces and input instance values; the three regression targets are the 1) time required by the online heuristic to find a solution, 2) the amount of memory, and 3) the solution quality. These ML models are then embedded in the optimization problem, which has the purpose of providing the optimal combination in terms of algorithm configuration and hardware dimensioning, given a set of user-specified constraints (e.g., bounding the run-time of the algorithm of obtaining solutions with quality higher than a threshold).

## Repository Content
This git repository is organized in the following directories:
- `./graphs/`: results of the ML models with different prediction targets (scatter plots depicting predicted versus true target);
- `./experimental_results/`: results of the comparison with a baseline (heuristic algorithm).