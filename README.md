# Safe & Explainable AI — Public Summary

**Author:** Pouya Bathaie Pourmand  
**Focus:** Reliability and interpretability of neural predictors for safety-critical systems.

## What is here (public-safe)
This repository provides a public-safe summary of experiments from my MSc work. No proprietary models or raw datasets are included. Only derived, non-sensitive results and human-readable explanations are provided.

## Key Results (summary)
- Random Forest: ~98% accuracy (best balance)
- Decision Tree (depth=8): ~97.5% (slight overfitting risk)
- KNN: ~95% (tends to overpredict success)
- Top features: Orientation (θ) and Linear Velocity (v)

## Included files (public)
- `results/summary_table.csv` — per-model success rates and average final distance
- `results/model_metrics.csv` — evaluation metrics for interpretable supervisors
- `results/feature_importances.txt` — final feature importance numbers
- `results/extracted_rules.txt` — excerpt of decision rules
- `figures/` — visual summaries (PNG)

## Disclaimer
Models, raw data and training scripts are confidential and not included here. This repo provides only derived summaries and images suitable for public sharing.
