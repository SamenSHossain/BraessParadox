# Braess' Paradox: From Classical Traffic Theory to Predictive Machine Learning

## 📌 Project Overview
This repository contains a comprehensive Jupyter Notebook (`BraessParadox.ipynb`) that explores **Braess' Paradox**—a counter-intuitive phenomenon where adding a new road to a traffic network can actually slow everyone down. 

The project is structured as an end-to-end pipeline that moves from demonstrating the classical theoretical math of the paradox, to solving it via optimization, and finally training a machine learning model to predict traffic behavior on entirely new, unseen city networks.

---

## 🏗️ Project Pipeline & Structure

The notebook is divided into four main sections:

### 1. The Theoretical Foundation (The Problem)
* **Objective:** Introduce and mathematically prove Braess' Paradox.
* **Details:** Simulates a classic 4-node network and demonstrates the difference between selfish routing (Wardrop/Nash Equilibrium) and cooperative routing (Social Optimum). It proves that adding a "shortcut" increases the total system cost and individual travel times.

### 2. Convex Optimization (The Mathematical Solution)
* **Objective:** Scale up the traffic problem and implement mitigation strategies.
* **Details:** Formulates the traffic assignment problem as a convex optimization program (Beckmann formulation) using advanced solvers. It calculates **Pigouvian tolls/subsidies**—mathematical pricing applied to specific roads to force selfish drivers into socially optimal, system-benefiting routes.

### 3. Graph-Theoretic Feature Extraction (The Data Engineering)
* **Objective:** Bridge theoretical network math with predictive machine learning.
* **Details:** Loads complex, real-world road network topologies and distills them into a 28-column feature matrix. It extracts mathematical properties like network density, diameter, average clustering, spectral radius, and flow entropy so that a machine learning model can process them.

### 4. Machine Learning & Generalization (The Predictive Model)
* **Objective:** Predict traffic behavior on unseen networks without running computationally heavy simulations.
* **Details:** Builds a **Stacking Ensemble** meta-learner (combining Ridge Regression and Gradient Boosting). It trains the model on the extracted topological features to instantly predict the severity of the paradox and optimal tolls for entirely *new* road networks. Evaluated using Leave-One-Topology-Out Cross-Validation (LOTO-CV).

---

## 🚀 Summary
In short, this notebook **demonstrates a traffic paradox, mathematically solves it using road pricing, and then trains an AI to predict that solution for any new road network.**
