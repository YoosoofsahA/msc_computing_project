# MSc Computing Final Project

**Project Title**: Predicting Extubation Failure in Intensive Care: The Development of a Novel, End-to-End Actionable and Interpretable Prediction System  
**Institution**: Imperial College London, 2024

## Project Overview

This repository contains the code and related resources for the MSc Computing final project titled **"Predicting Extubation Failure in Intensive Care: The Development of a Novel, End-to-End Actionable and Interpretable Prediction System."** The project was completed at **Imperial College London** in 2024.

This thesis aims to explore the development of a novel, end-to-end actionable and interpretable prediction system that effectively leverages time-series data, empowering clinicians to confidently assess extubation failure risk.

### Objectives:
1. Focus models specifically on predicting extubation failure, distinct from extubation readiness or weaning timing.
2. Compare the performance of **LSTM** and **TCN** models with a non-temporal baseline, introducing TCNs as a novel approach for this prediction.
3. Ensure model interpretability is prioritized for clinical transparency.
4. Collaborate with clinicians to implement rigorous data pre-processing that preserves patient dynamics for real-world application.

### Key Contributions

#### Data Pre-processing
- **Clinically Informed Feature Selection**: We introduced a systematic approach to feature selection, balancing popularity in precedent studies and real-world clinical considerations, using the WAVE study as a benchmark.
- **Clinically Relevant Time Window**: Prioritized a 6-hour window before extubation for data extraction to reflect clinical practice in extubation decision-making. Surprisingly, this clinically relevant time frame has not been used in previous work.
- **Stratified Train/Test Split**: Stratified the train/test split based on the proportion of synthetic data required, ensuring the model was not biased toward ill-representative synthetic patterns, an approach not seen in previous studies.
- **Novel Resampling and Interpolation**: Developed a bespoke resampling strategy, splitting features into subsets based on the average observed frequency. Linear interpolation was used to better represent temporal patterns, whereas forward fill was traditionally used, minimizing the creation of synthetic data patterns that could bias the model.
- **Masking**: For missing values, we filled them with NaNs and implemented masking to preserve data integrity. This allowed models to handle missing data more effectively and minimized synthetic data creation.

#### Model Development
- **Exploration of Temporal Architectures**: Our work is the first to explore using a Temporal Convolutional Network (TCN) to predict extubation failure. We compared the performance of two inherently different architectures (LSTM and TCN) to assess their strengths and weaknesses.
- **Fused Decision Architecture**: Guided by data requirements, we developed Fused LSTM and TCN models to integrate multiple feature subsets resampled to different rates. This novel approach enabled us to handle various input formats.
- **Static Data Integration with FFNN**: While integrating static data is common, an FFNN has not been explicitly used when predicting extubation failure. This allowed us to handle the fundamental differences between tabular and time-series data, ensuring static context was captured.
- **Bespoke Hyperparameters to Handle Class Imbalance**: To address the inherent class imbalance in the data, we implemented a bespoke sampling method and tuned weighted loss parameters during optimization. This provided a more dynamic, data-driven solution beyond traditional techniques.

#### Model Interpretability
- **Challenges with Traditional Interpretability Methods**: Our work highlighted the limitations of popular interpretability techniques (e.g., SHAP and LIME) when applied to complex, temporally dependent, and synthetic-data-contingent models. This is a crucial foundation for future work.
- **Feature Ablation with Clinical Insights**: We implemented feature ablation as a practical alternative, which has not been used before in extubation failure prediction. This provided a path toward model transparency that can be justified or questioned through clinical insights.


## Folder Structure

```bash
├── 01_background_report/EDA/      # Exploratory Data Analysis (EDA) and background research for the project
├── 02_data_analysis/              # Data analysis notebooks and scripts, including MIMIC-IV data analysis
│   └── mimic/data_analysis/notebooks/  # Jupyter notebooks for in-depth data analysis
├── 03_model_development/          # Code related to developing prediction models, including LSTM, TCN, etc.
├── 04_ensemble_methods/           # Scripts and code for implementing ensemble methods to improve prediction performance
├── 05_code_for_figures/           # Code used to generate the figures and visualizations in the thesis
└── README.md                      # Project documentation

