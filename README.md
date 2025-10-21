# Safe & Explainable AI — Public Summary

**Author:** Pouya Bathaie Pourmand  
**Focus:** Reliable and interpretable neural models for safety-critical systems  
**Status:** Ongoing MSc Research — Part of the REXASI-PRO project (Safe AI for autonomous wheelchairs)

---

## Related Work
- 🧠 *Safe and Explainable Trajectory Prediction for Smart Wheelchairs* — Mini research summary (this repository)  
- 📘 *MSc Thesis (in progress): Interpretable AI Models for Safety Supervision*

---

## Project Overview
This project investigates how to make neural network models more **reliable and understandable** when used in safety-critical systems such as **autonomous or smart wheelchairs**.  
The main goal is to understand **when and why** a neural network might generate unsafe outputs and to design an interpretable supervisor that can **detect risky predictions before they cause unsafe behavior**.  

Part of this work is being carried out within the **REXASI-PRO** research framework, which focuses on creating trustworthy and explainable AI for robotics and assistive mobility.  
The neural models used in this study were **pre-trained by an industrial partner**, and the analysis was performed only on their **predicted trajectories** — no proprietary data or code is shared in this repository.

---

## Method
- Each input scenario is represented by three parameters: **orientation (θ)**, **linear velocity (v)**, and **rotational velocity (ω)**.  
- The pre-trained neural networks predict a trajectory toward a target goal based on these parameters.  
- The **Euclidean distance to the goal** is used to label each trajectory as “Success” or “Fail.”  
- Because the dataset was imbalanced (more “Fail” cases), **SMOTE** was applied only on the training set to balance the classes.  
- Then, **interpretable models** — *Decision Tree*, *Random Forest*, and *KNN* — were trained to identify unsafe cases and explain which input regions are likely to lead to unsafe motion.  

---

## Results and Insights
- **Random Forest** achieved the most stable and balanced performance with around **98% accuracy**.  
- **Decision Tree (depth=8)** reached about **97.5% accuracy**, generating clear and human-readable rules, though with slight overfitting.  
- **KNN** achieved around **95% accuracy**, showing good generalization but a tendency to overpredict “Success.”  
- The most important features for detecting unsafe trajectories were **Orientation (θ)** and **Linear Velocity (v)**, while **Rotational Velocity (ω)** had a smaller impact.  

These findings confirm that adding explainable models on top of deep networks can successfully identify risky inputs and improve trust in safety-critical systems.

---

## Applications
This work demonstrates how **explainable and trustworthy AI** can support decision-making in autonomous systems such as smart wheelchairs, mobile robots, and industrial control units.  
The same principles can be extended to **robotics, navigation, and safety monitoring**, where transparency and reliability are essential.

---

## Files in this Repository
- `results/summary_table.csv` — success rates and average distances for each neural model  
- `results/model_metrics.csv` — accuracy and precision of interpretable models  
- `results/feature_importances.txt` — the most relevant input features  
- `results/extracted_rules.txt` — examples of decision rules from the trained tree models  
- `figures/` — visual summaries such as feature importance and confusion matrices  

---

## Disclaimer
This repository includes only **public-safe summaries and derived results**.  
The original datasets, pre-trained models, and company-specific implementations are **confidential and not shared here**.  
The content provided is for educational and demonstrative purposes to illustrate methodology and explainable analysis.
