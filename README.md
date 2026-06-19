# Comparative Simulation of PSO and ABC for Swarm UAV Path Planning

This repository contains a Google Colab notebook for a comparative simulation of Particle Swarm Optimization (PSO) and Artificial Bee Colony (ABC) algorithms for swarm UAV path planning. The experiment was prepared for an Edge Computing lab report, with emphasis on the effect of UAV count and waypoint count on path planning performance.

Swarm UAV path planning can be formulated as an optimization problem in which each UAV must move from a start point to a goal point while avoiding obstacles and maintaining safe separation from other UAVs. In an edge computing context, the path planning process can be executed near the UAV system, such as on an edge node, gateway, or ground station, to reduce decision latency.

This simulation focuses on a two-dimensional environment with circular obstacles. PSO and ABC are compared using the same objective function, search space, scenario configuration, number of iterations, and number of independent runs.

## Objectives

The objectives of this repository are:

1. To implement PSO and ABC for swarm UAV path planning.
2. To compare both algorithms under different numbers of UAVs and waypoints.
3. To evaluate the algorithms using path cost, path length, obstacle collision, separation violation, execution time, success rate, and convergence behavior.
4. To generate raw simulation data that can be attached to a lab report.

## Simulation Scenarios

The experiment uses five simulation scenarios.

| Scenario | Number of UAVs | Number of Waypoints | Purpose |
|---|---:|---:|---|
| S1 | 1 | 1 | Baseline case, close to the basic path planning example |
| S2 | 1 | 3 | Effect of increasing waypoint count |
| S3 | 3 | 1 | Effect of increasing UAV count |
| S4 | 3 | 3 | Multi-UAV and multi-waypoint case |
| S5 | 5 | 3 | Scalability stress test |

## Objective Function

Each candidate solution is evaluated using a penalty-based objective function:

```text
J = L + P_collision + P_separation + P_smoothness
```

where:

| Component | Description |
|---|---|
| L | Total path length of all UAVs |
| P_collision | Penalty for obstacle intersection |
| P_separation | Penalty for unsafe distance between UAVs |
| P_smoothness | Penalty for sharp turns or non-smooth paths |

A lower value of `J` indicates a better path configuration.

## Algorithms

### Particle Swarm Optimization

PSO represents each candidate path as a particle. Each particle updates its position based on its previous velocity, personal best solution, and global best solution.

### Artificial Bee Colony

ABC represents each candidate path as a food source. The search process is carried out through employed bee, onlooker bee, and scout bee phases to balance local exploitation and global exploration.

## Evaluation Metrics

The algorithms are evaluated using the following metrics:

| Metric | Description |
|---|---|
| Best cost | Best objective value found in a scenario |
| Mean cost | Average objective value over independent runs |
| Standard deviation | Stability of the algorithm over repeated runs |
| Path length | Total UAV path length |
| Collision count | Number of obstacle collision cases |
| Separation violation | Number of unsafe inter-UAV distance cases |
| Execution time | Computation time of the algorithm |
| Success rate | Percentage of valid runs |
| Convergence curve | Best objective value across iterations |

## Experimental Setting

The default experimental setting is:

| Parameter | Value |
|---|---:|
| Algorithms | PSO and ABC |
| Independent runs | 30 |
| Iterations | 100 |
| Population size | 50 |
| Environment | 2D search area |
| Obstacles | Circular obstacles |
| Output format | CSV and PNG |

The parameters can be adjusted directly in the notebook.

## How to Run

1. Open the notebook in Google Colab.
2. Run all cells from top to bottom.
3. Wait until the simulation finishes for all scenarios and algorithms.
4. Download the generated output files.
5. Use the CSV files as raw simulation attachments and selected figures for the lab report.

## Outputs

| File | Description |
|---|---|
| `raw_simulation_results.csv` | Raw results for each algorithm, scenario, and run |
| `raw_convergence_history.csv` | Best cost history per iteration |
| `summary_results.csv` | Aggregated result table |
| `scenario_winner_summary.csv` | Algorithm comparison per scenario |
| `uav_path_planning_outputs.zip` | Compressed output package |

## References

1. ITU-T Recommendation Y.2060, Overview of the Internet of Things, 2012.
2. S. Lin, F. Li, X. Li, and Z. Yang, Improved Artificial Bee Colony Algorithm Based on Multi-Strategy Synthesis for UAV Path Planning, IEEE Access, 2022.
3. A. Sonny, Y. S. Reddy, and L. R. Cenkeramaddi, Autonomous UAV Path Planning Using Modified PSO for UAV-Assisted Wireless Networks, IEEE Access, 2023.
4. V. T. Hoang, M. D. Phung, T. H. Dinh, and Q. P. Ha, Angle-Encoded Swarm Optimization for UAV Formation Path Planning, IEEE/RSJ International Conference on Intelligent Robots and Systems, 2018.
