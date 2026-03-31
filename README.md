# Braess' Paradox Notebook Overview

Based on the contents of the `BraessParadox.ipynb` notebook, the project is structured to transition from demonstrating the theoretical mathematical foundations of Braess' Paradox to optimizing network traffic, and finally applying machine learning to generalize these findings to real-world network topologies. 

Here is the explanation of the purpose of each main code block in the overall notebook:

### 1. Mathematical Foundation & Demonstration of Braess' Paradox
* **Purpose:** This block establishes the fundamental proof of Braess' Paradox using a classic 4-node/5-edge network (Source to Sink). 
* **How it works:** It uses fixed-point iteration to calculate both the Wardrop Equilibrium (selfish routing, or Nash Equilibrium) and the Social Optimum (cooperative routing). 
* **Overall Contribution:** It explicitly demonstrates the paradox by showing that adding a zero-latency "shortcut" edge actually increases the total system cost and individual travel times. It concludes by computing the "Price of Anarchy" (PoA) to quantify how much worse selfish routing is compared to the social optimum.

### 2. Convex Optimization & Pigouvian Subsidies (Road Pricing)
* **Purpose:** This block scales the problem up by formulating the traffic assignment problem as a convex optimization program (the Beckmann formulation). 
* **How it works:** Instead of simple fixed-point iteration, it uses advanced optimization algorithms (like L-BFGS-B) to find the Social Optimum and Wardrop Equilibrium. Furthermore, it calculates analytic Pigouvian tolls/subsidies (where Marginal Social Cost = Marginal Private Cost + Subsidy). 
* **Overall Contribution:** This block serves as the mitigation strategy for the paradox. It sets up a Sequential Convex Programming (SCP) framework to figure out how to mathematically apply tolls or subsidies to force selfish drivers into the socially optimal routing. 

### 3. Graph-Theoretic Feature Extraction
* **Purpose:** This block is responsible for preparing the data to bridge theoretical network math with predictive machine learning.
* **How it works:** It loads in 5 real-world network topologies and extracts a 28-column feature matrix. These features include mathematical properties of the graphs such as the number of nodes, edges, network density, diameter, average clustering, spectral radius, and flow entropy.
* **Overall Contribution:** By extracting these quantitative features, the notebook translates complex, varying network structures into structured tabular data that a machine learning algorithm can process.

### 4. Machine Learning: Stacking Ensemble & Generalization
* **Purpose:** This final block builds a predictive model to estimate network behavior (like the Price of Anarchy or optimal tolls) on unseen topologies without needing to run computationally heavy optimization simulations.
* **How it works:** It implements a Stacking Ensemble meta-learner. It uses Ridge Regression and Gradient Boosting as base learners, and another Ridge regressor as the meta-learner. 
* **Overall Contribution:** It evaluates the model using Leave-One-Topology-Out Cross-Validation (LOTO-CV), ensuring that the model can successfully generalize to entirely new, unobserved network holdouts based purely on the topological features extracted in the previous step.
