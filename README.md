# Influence Maximization in Social Networks

This repository contains a two-phase exploratory research project focused on simulating information diffusion and solving the Influence Maximization (IM) problem within social networks. 

## Project Overview
The project explores how information, behaviors, or contagions spread through a network and attempts to find the optimal starting nodes (seeds) to maximize this spread. It is structured into two main phases:
1. **Phase 1:** Building a simulation environment to evaluate foundational information diffusion models and centrality-based seed selection.
2. **Phase 2:** Implementing Swarm Intelligence metaheuristics to efficiently solve the NP-hard Influence Maximization problem on large-scale networks.

## Datasets
The models and algorithms were evaluated using real-world network datasets from the Stanford Network Analysis Project (SNAP):
* **ego-Facebook:** An undirected graph representing dense social circles and community clusters.
* **wiki-Vote:** A directed graph representing hierarchical administrator voting.
* **ca-GrQc:** A directed graph representing scientific collaborations.
* **p2p-Gnutella30:** A massive directed peer-to-peer file-sharing network used for scalability benchmarking.

## Phase 1: Information Diffusion Models
The first phase focuses on building a computational foundation to simulate propagation dynamics.

**Models Implemented:**
* **Threshold Models:** Linear Threshold (LT), Majority Threshold (MT), Small Threshold (ST), and Unanimous Threshold (UT).
* **Cascading Models:** Independent Cascade (IC), Decreasing Cascade (DC), and Generalized Cascade (GC).
* **Epidemic Models:** SIR, SIS, and SIRS compartmental models.
* **Competitive Models:** Distance-Based, Wave Propagation, Weight-Proportional (WPT), and Separate Threshold (Asymmetric) models.

**Key Features:**
* Developed an object-oriented simulation environment in Python.
* Utilized a Monte Carlo execution engine to handle stochastic cascade variance.
* Evaluated baseline seed selection using Degree, Closeness, and Betweenness Centrality.

## Phase 2: Swarm Intelligence Metaheuristics
The second phase tackles the computational bottleneck of traditional Monte Carlo simulations by introducing advanced metaheuristics to find near-optimal seed sets.

**Algorithms Implemented:**
* **Ant Colony Optimization (ACO-IM):** Employs a constructive search strategy where artificial ants build seed sets node-by-node, guided by pheromone trails and localized heuristics.
* **Discrete Particle Swarm Optimization (DPSO):** Utilizes a navigational search strategy using a Sigmoid Transformation and Top-k filter to map continuous vector velocities to discrete network nodes.

**Key Features:**
* Replaced computationally heavy simulations with a fast Local Influence Heuristic ($EDV_{[2]}$) to estimate spread scalability.
* Benchmarked the trade-offs between solution accuracy and execution speed across Swarm architectures.

## Key Learnings
* **Centrality Trade-offs:** Betweenness Centrality finds the best influential "bridge" nodes but is computationally unfeasible for large-scale networks due to its $\mathcal{O}(VE)$ runtime. Degree Centrality provides an optimal compromise, offering $>90\%$ of global centrality performance in just $\mathcal{O}(V+E)$ time.
* **Network Topology Impact:** Cascading models can struggle in highly clustered networks due to "echo chambers," whereas Threshold models (like LT) thrive on overlapping community triangles and rapid peer pressure.
* **Swarm Intelligence Trade-offs:** ACO-IM achieves a higher absolute influence spread by utilizing precise, localized heuristic searches. Conversely, DPSO executes significantly faster and scales better to massive networks due to its vectorized mathematical approach.
* **Competitive Advantage:** Strategically securing structural hub nodes early on can effectively block and surpass a competing contagion, even if the competitor has a naturally higher viral transmission probability.

## Acknowledgements
I would like to express my sincere gratitude to my project supervisor, **Prof. Bhaskar Biswas**, for his invaluable guidance, support, and insights throughout the development of this research project.
