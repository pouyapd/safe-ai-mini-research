README — Safe & Explainable AI for Trajectory Prediction (Public Summary, 2025 Update)

Author: Pouya Bathaie Pourmand
Affiliation: MSc in Artificial Intelligence — University of Genoa / CNR Italy
Project: REXASI-PRO — Reliable & Explainable AI for Smart Mobility
Focus: Understanding and supervising neural trajectory-prediction models to ensure safety and robustness in autonomous mobility systems.

1. Overview

This repository contains a public summary of my MSc research on safe and explainable AI for trajectory prediction, with applications to smart wheelchairs and other mobile robots.

The goal of the project is:

to analyse when and why trajectory-prediction networks fail,

to identify unsafe input conditions,

and to design interpretable supervisors that detect risky outputs before the system behaves unsafely.

The neural networks used here were pre-trained by an industrial partner.
My work focuses solely on analysing their behaviour, stability, and failure modes — no proprietary datasets or models are shared.

2. Problem Setting

Each scenario is defined by three controllable inputs:

Orientation (θ)

Linear velocity (v)

Rotational velocity (ω)

Given these parameters, a neural model predicts a trajectory toward a target goal.
A prediction is labelled as:

Success → final position close to the goal

Failure → trajectory drifts away or diverges

This framework enables us to study how input conditions influence stability and safety.

3. Experiments (2025 Update)
Experiment 1 — Input Sensitivity (Fixed Goal)

Purpose: Identify which input regions (θ, v, ω) are more likely to produce unsafe predictions.

Key Findings:

Orientation (θ) is the dominant risk factor.
Failures sharply increase near ±π (robot facing backwards).

Higher velocities or rotations have secondary influence.

Model variability is strong:

closs1 shows the largest deviations and most failures

closs2 is consistently stable

Even when failing, closs2 stays close to the goal (low failure distance).

Outputs included:

θ / v / ω vs final distance plots

Success-rate bins for each input dimension

Failure-distance distribution

Associated CSV tables

Experiment 2 — Goal Difficulty (Fixed Start)

Purpose: Understand which goal positions are easy or difficult for the models.

Key Findings:

Goals at (0.5, 0.5) and (1.5, –0.5) produce almost 100% success across models.

The goal at (1.0, 0.0) is significantly harder for every model.

The difficulty map clearly separates safe vs challenging goal regions.

Outputs included:

Success heatmap per goal

Difficulty map

Summary tables

Failure-Distance Analysis

Beyond success/failure, we measure how severe a failure is.

closs1 can diverge up to ~1 meter from the target

closs2 remains within ~0.33 m → “near-correct” behaviour even in failed attempts

This metric is crucial for safety monitoring, as not all failures are equally risky.

4. Explainable AI Supervisor

To interpret and classify neural outputs, the following ML models were trained:

Decision Tree (depth=8)

Random Forest

KNN

These models use only the input parameters (θ, v, ω) and the success labels generated from neural predictions.

Performance summary:

Random Forest: ~98% accuracy, most stable

Decision Tree: ~97.5%, provides clear human-readable rules

KNN: ~95%, slightly biased toward predicting Success

Main contributing features:

Orientation (θ)

Linear Velocity (v)

Rotational Velocity (ω) — lower impact

These interpretable models help define risk zones and improve safety monitoring.

5. Repository Contents
results/
    summary_table.csv
    model_metrics.csv
    feature_importances.txt
    extracted_rules.txt

trajectory_analysis/
    exp1_input_sensitivity/
        exp1_analysis.ipynb
        theta_vs_distance.png
        velocity_vs_distance.png
        omega_vs_distance.png
        failure_distance_boxplot.png
        exp1_theta_bins.csv
        exp1_velocity_bins.csv
        exp1_omega_bins.csv

    exp2_goal_difficulty/
        exp2_analysis.ipynb
        goal_success_heatmap.png
        goal_difficulty_map.png
        goal_success_table.csv

    failure_distance_stats.csv

figures/
    (visual summaries, feature importance plots, confusion matrices, etc.)

6. Applications

The methods in this project support:

Safe decision-making in smart wheelchairs

Trajectory supervision in mobile robots

Safety layers in navigation systems

Model-monitoring and OOD detection pipelines

The principles are general and apply to any system where trustworthy and interpretable AI is required.

7. Disclaimer

This repository includes only:

High-level summaries

Derived results

Public-safe visualizations

All proprietary datasets, weights, and internal implementations remain confidential.
