# Safe & Explainable AI for Trajectory Prediction (Public Summary, 2025 Update)

**Author:** Pouya Bathaie Pourmand  
**Affiliation:** MSc in Artificial Intelligence — University of Genoa / CNR Italy  
**Project:** REXASI-PRO — Reliable & Explainable AI for Smart Mobility  
**Focus:** Understanding and supervising neural trajectory-prediction models to ensure safety and robustness in autonomous mobility systems.

---

## 1. Overview
This repository contains a public summary of my MSc research on **safe and explainable AI for trajectory prediction**, with applications to smart wheelchairs and mobile robots.

The goal is to:
- analyse **when and why** neural predictors fail,  
- identify **unsafe input conditions**,  
- and design **interpretable supervisors** that detect risky outputs before unsafe actions occur.

The neural models analysed here were **pre-trained by an industrial partner**.  
Only behaviour analysis and failure characterization are included — **no proprietary data or models** are shared.

---

## 2. Problem Setting
Each scenario is defined by three controllable inputs:

- **Orientation (θ)**
- **Linear velocity (v)**
- **Rotational velocity (ω)**

Given these parameters, a network predicts a **trajectory** toward a target goal.  
A prediction is labelled as:

- **Success** → ends sufficiently close to goal  
- **Failure** → deviates significantly or diverges

This allows evaluation of stability and unsafe behaviour modes.

---

## 3. Experiments (2025 Update)

### Experiment 1 — Input Sensitivity (Fixed Goal)
Purpose: Identify unsafe regions in the input space (θ, v, ω).

**Key findings:**
- **Orientation (θ)** is the strongest risk factor  
  → failures increase near ±π (robot facing backwards)
- High **v** or **ω** have secondary effects
- **closs1**: most unstable  
- **closs2**: most stable; low failure distance even when failing

**Included outputs:**
- θ / v / ω vs distance plots  
- Success-rate bins  
- Failure-distance boxplot  
- CSV summaries  

---

### Experiment 2 — Goal Difficulty (Fixed Start)
Purpose: Evaluate which goal positions are more difficult.

**Key findings:**
- Goals **(0.5, 0.5)** and **(1.5, –0.5)** → almost always successful  
- Goal **(1.0, 0.0)** → systematically difficult  
- Difficulty maps separate safe vs challenging regions

**Included outputs:**
- Success heatmap  
- Difficulty map  
- Summary tables  

---

### Failure-Distance Analysis
Beyond success/failure, the analysis measures **how severe** failures are.

- **closs1**: failures up to ~1 m  
- **closs2**: failures mostly under ~0.33 m  

This metric is essential for safety supervision.

---

## 4. Explainable AI Supervisor
Interpretable models trained using labels derived from neural predictions:

- **Decision Tree (depth=8)**  
- **Random Forest**  
- **KNN**

**Performance:**
- Random Forest → ~98% accuracy  
- Decision Tree → ~97.5% and provides human-readable rules  
- KNN → ~95%, slightly biased toward “Success”

**Feature importance:**
1. Orientation (θ)  
2. Linear velocity (v)  
3. Rotational velocity (ω)

These highlight risk zones and improve system trust.

---

## 📂 Repository Contents

The project file structure is organized as follows:

```text
.
├── results/
│   ├── summary_table.csv          # Aggregate metrics for all runs
│   ├── model_metrics.csv          # Detailed performance metrics of the model
│   ├── feature_importances.txt    # Ranked list of input features
│   └── extracted_rules.txt        # Logical rules extracted from the model
│
├── trajectory_analysis/
│   ├── exp1_input_sensitivity/
│   │   ├── exp1_analysis.ipynb          # Notebook for input sensitivity analysis
│   │   ├── theta_vs_distance.png        # Plot: Theta angle over distance
│   │   ├── velocity_vs_distance.png     # Plot: Velocity profile over distance
│   │   ├── omega_vs_distance.png        # Plot: Angular velocity over distance
│   │   ├── failure_distance_boxplot.png # Distribution of failure distances
│   │   ├── exp1_theta_bins.csv          # Binned data for theta analysis
│   │   ├── exp1_velocity_bins.csv       # Binned data for velocity analysis
│   │   └── exp1_omega_bins.csv          # Binned data for omega analysis
│   │
│   ├── exp2_goal_difficulty/
│   │   ├── exp2_analysis.ipynb          # Notebook for goal difficulty analysis
│   │   ├── goal_success_heatmap.png     # Visual heatmap of success rates
│   │   ├── goal_difficulty_map.png      # Map visualizing difficulty zones
│   │   └── goal_success_table.csv       # Raw data for success rates
│   │
│   └── failure_distance_stats.csv       # Overall statistical summary of failure distances
│
└── figures/
    └── (feature importance, confusion matrices, etc.)

---

## 6. Applications
This work supports:

- Safety monitoring in smart wheelchairs  
- Trajectory supervision in mobile robots  
- Navigation risk analysis  
- Model-monitoring and OOD detection pipelines  

Core principles generalize to any **safety-critical AI system**.

---

## 7. Disclaimer
This repository contains only **derived results, summaries, and public-safe visualizations**.  
No confidential datasets, weights, or industrial code are included.

