# Constrained Hardware Dimensioning for Online Algorithms
Experimental evaluation.

We propose an approach for automatic hardware dimensioning and algorithm configuration of two state-of-the-art online algorithms under an heterogeneous set of constraints.
We rely on the integration of Machine Learning models within an optimization problem, following the Empirical Model Learning paradigm by Lombardi et al, "Empirical decision model learning", 2017. Machine Learning is used for benchmarking the target algorithm on different hardware configurations and optimization is used to find the optimal matching of computing resources and algorithm configuration, while respecting user-defined constraints (e.g., cost, time, solution quality). The empirical evaluation shows that our method can find optimal combinations, in terms of algorithm configuration and hardware dimensioning, for new, unseen data instances, while its flexibility allows the adoption of different constraints and/or objectives, as required by users.

## Approach Detail

We propose an optimization method composed of an optimization model and two sets (one for each of the algorithms) of three ML regression models, each one devoted to predicting a specific target, given a certain input instance and a certain value for the decisional variables of the algorithms; the three regression targets are the 1) time required by the online heuristic to find a solution, 2) the amount of memory, and 3) the solution quality. These ML models are then embedded in the optimization problem, which has the purpose of providing the optimal combination in terms of algorithm configuration and hardware dimensioning, given a set of user-specified constraints (e.g., bounding the run-time of the algorithm of obtaining solutions with quality higher than a threshold).

## Repository Content
This git repository is organized in the following directories:
- `./graphs/`: results of the ML models with different prediction targets (scatter plots depicting predicted versus true target);
- `./DT10_err_dists/`: graphs for the distribution of the prediction error for the three targets obtained using the same ML models embedded in the optimization model (Decision Trees with maximum depth == 10); the predictions were done on the same validation set using during the training phase;
- `./experimental_results/`: results of the trials conducted using the optimizations models produced during the experimentations; the files containing the suffix "_std*_perc*" represent trials conducted using models with increased robustness (see section 3.4); these results are organized in:
  - `./experimental_results/algorithm_configuration_only_model`: csv files (both for ANTICIPATE and CONTINGENCY) for the trials, expressed in terms of imposed instance, imposed bounds on time and memory (if any), optimized decisional variable and resulting values for time, memory and cost; 
  - `./experimental_results/algorithm_selection_configuration_model`: csv files following the same structure described above, with the exception that since we're also selecting the best algorithm, they contain the targets and the decisional variable for both algorithms, and also two additional columns, each one representing the binary variable for the corresponding algorithm (see Eq. 1 and 2);