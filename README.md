# Boom: Trajectory Unknown Challenge
Physics-Informed Machine Learning for Asteroid Impact Ejecta Prediction and Inverse Design

---

# Pipeline

Impact Parameters
        ↓
Physics Feature Engineering
        ↓
Ensemble ML Models
        ↓
Prediction Validation
        ↓
Explainable AI (SHAP)
        ↓
Bayesian Optimization
        ↓
Inverse Design Scenarios

# Project Overview

This project develops a physics-informed machine learning framework to model fragmentation and material displacement caused by asteroid impacts. The goal is to predict ejecta outcomes from impact parameters and design impact scenarios that satisfy specific debris constraints.

The solution integrates **machine learning, physics-based feature engineering, explainable AI, and optimization techniques** to address both tasks of the challenge:

• **Forward Prediction** – Predict ejecta outcomes for unseen impact scenarios.  
• **Inverse Design** – Identify impact parameters that produce desired fragment size and ejecta displacement characteristics.

---

# Dataset

The dataset contains simulated asteroid impact events from the **Mox-95 planetary system**.

## Input Parameters

The model uses the following impact parameters:

- porosity  
- atmosphere  
- gravity  
- coupling  
- strength  
- shape_factor  
- energy  
- angle_rad  

## Output Variables

The predicted ejecta outcomes are:

- **P80** – fragment size distribution metric  
- **fines_frac** – fraction of fine particles  
- **oversize_frac** – fraction of large fragments  
- **R95** – maximum ejecta distance  
- **R50_fines** – median distance of fine particles  
- **R50_oversize** – median distance of large fragments  

---

# Methodology

## Physics-Informed Feature Engineering

To capture the physical relationships governing impact fragmentation, additional features were derived:

- material_resistance = strength × (1 − porosity)  
- impact_scaling = energy / strength  
- effective_energy = energy × coupling  
- angle_energy = energy × sin(angle_rad)  
- energy_gravity = energy / gravity  
- mobility_factor = energy / (gravity × strength)

These engineered features allow the model to incorporate **domain knowledge from impact physics**.

---

## Ensemble Machine Learning

An ensemble of machine learning models was used to improve prediction accuracy and robustness.

Models used:

- Random Forest  
- Extra Trees  
- XGBoost  

Predictions from the models are averaged to generate the final ejecta predictions.

---

## Model Validation

The model was evaluated using multiple validation techniques:

- Predicted vs Actual comparison  
- Prediction error distribution  
- Feature importance analysis  

These evaluations confirm that the model accurately captures the relationship between impact parameters and ejecta outcomes.

---

## Explainable AI

To interpret model behavior and ensure transparency, several explainability methods were applied:

- Feature importance visualization  
- SHAP summary analysis  
- SHAP dependence plots  
- Partial dependence plots  

These analyses reveal that physics-derived features such as **material resistance** and **impact scaling** play a dominant role in determining fragment size distribution.

---

## Inverse Design

The challenge also requires identifying impact scenarios that produce specific ejecta outcomes.

### Constraints

96 ≤ P80 ≤ 101  
R95 ≤ 175  

Inverse design was implemented using:

- Bayesian optimization  
- Random candidate scenario generation  
- Pareto-based scenario selection  

The final algorithm selects **20 optimized impact scenarios** that satisfy the constraints while minimizing impact energy and ejecta displacement.

---

# Results

The project produces the two required submission files.

## Forward Prediction

prediction_submission.csv

This file contains predicted ejecta outcomes for the provided test dataset.

---

## Inverse Design

design_submission.csv

This file contains **20 optimized impact parameter scenarios** that satisfy the challenge constraints.

---

# Repository Structure

boom-impact-ai/

├── boom_model.ipynb  
├── prediction_submission.csv  
├── design_submission.csv  
├── requirements.txt  
└── README.md  

---

# Technologies Used

- Python  
- NumPy  
- Pandas  
- Scikit-learn  
- XGBoost  
- SHAP  
- Matplotlib  
- Seaborn  
- scikit-optimize  

---

## Hardware Requirements

The proposed solution is computationally efficient and does not require specialized hardware such as GPUs.

### Training Environment

- **Operating System:** Microsoft Windows 11 Home (Version 10.0.26100)
- **Processor:** Intel Core i7-6700HQ CPU @ 2.60 GHz (4 cores, 8 threads)
- **RAM:** 16 GB
- **System Architecture:** x64-based PC
- **Machine:** Lenovo IdeaPad Y700-15ISK
- **Python Version:** Python 3.12

### Hardware Usage

The algorithm was developed and executed on a standard laptop without GPU acceleration.

- **GPU:** Not required
- **Compute:** CPU only

### Training Time

Training the ensemble machine learning model (Random Forest, Extra Trees, and XGBoost) takes approximately:

- **~1–3 minutes on CPU**

### Inference Performance

Prediction is very lightweight:

- Predicting ejecta outcomes for the entire test dataset (492 scenarios) takes **less than 1 second**.

### Inverse Design Optimization

The Bayesian optimization process used for inverse design typically completes within:

- **~2–5 minutes on CPU**

### Practicality

The algorithm can run efficiently on standard personal computers without requiring GPUs or specialized hardware. This makes the approach suitable for rapid experimentation, deployment, and application to other physics-driven modeling problems.

# Reproducibility

To reproduce the results:

1. Install dependencies

pip install -r requirements.txt

2. Run the notebook

boom_model.ipynb

The notebook will train the model and generate the submission files.

---

# Key Contributions

This project demonstrates:

- Physics-informed machine learning for fragmentation modeling  
- Ensemble learning for robust prediction  
- Explainable AI for interpreting model behavior  
- Optimization-based inverse design of impact scenarios  

Together these components create a comprehensive framework for **predicting and designing asteroid impact events**.

---

# Author

Aklesh Mishra
