# MSc Computing Final Project

**Project Overview**
This repository contains the code and related resources for the MSc Computing final project titled "Predicting Extubation Failure in Intensive Care: The Development of a Novel, End-to-End Actionable and Interpretable Prediction System". The project was completed at Imperial College London in 2024.

This thesis aims to explore the development of a novel, end-to-end actionable and interpretable prediction system that effectively leverages time-series data, empowering clinicians to confidently assess extubation failure risk. 

Specifically, our objectives are:
1. Focus models specifically on predicting extubation failure, distinct from extubation readiness or weaning timing
2. Compare the performance of LSTM and TCN models with a non-temporal baseline, introducing TCNs as a novel approach for this prediction
3. Ensure model interpretability is prioritised for clinical transparency
4. Collaborate with clinicians to implement rigorous data pre-processing that preserves patient dynamics for real-world application

**Key Contributions:**

Our system comprises three distinctive components: data pre-processing, model development, and interpreta- tion. Within each of these, our work has significantly contributed to advancing the field through innovative, data-driven, and clinically relevant approaches, as outlined below.


• Data Pre-processing
– Clinically Informed Feature Selection: We introduced a systematic approach to feature se- lection, balancing popularity in precedent studies and real-world clinical considerations with the WAVE study used as a benchmark.
– Clinically relevant Time Window: We prioritised a 6-hour window before extubation for data extraction to reflect clinical practice in extubation decision-making. This confirmed clinically rele- vant time frame is surprisingly not used in previous work.
– Stratified Train/Test Split: We stratified the train/test split based on the proportion of synthetic data required. This ensured the model was not biased toward ill-representative synthetic patterns, an approach not seen in previous studies.
– Novel Resampling and Interpolation: We created a bespoke resampling strategy, splitting features into subsets based on the average observed frequency to try and minimise the creation of synthetic data patterns, which would otherwise lead to model bias. Linear interpolation was used to better represent temporal patterns, whereas forward fill was traditionally used.
– Masking: Where features were missing any value, we filled them with NaNs and implemented masking to preserve data integrity. This allowed models to handle missing data more effectively and minimised synthetic data creation.

• Model Development
– Exploration of Temporal Architectures: Our work is the first to explore using a Temporal Convolutional Network (TCN) to predict extubation failure. We compared the performance of two inherently different architectures to assess their strengths and weaknesses.
– Fused Decision Architecture: Guided by the data requirements, we developed Fused LSTM and TCN models to integrate multiple feature subsets resampled to different rates. This novel approach enabled us to handle various inputs.
– Static data integration with FFNN: Although not the first to implement this for static data, an FFNN has not been explicitly used when predicting extubation failure. This enabled us to handle the fundamental difference between tabular and time-series data while ensuring static context was captured.
– Bespoke Hyperparameters to Handle Class Imbalance: To address the inherent imbalance in the data, we implemented a bespoke sampling method and weighted loss parameters to be tuned during optimisation. This moved beyond the traditional application of one technique or the other, providing a more dynamic data-driven solution.

• Model Interpretability
– Challenges with traditional interpretability methods: Our work highlighted the limitations of popular interpretability techniques (SHAP and LIME) when applied to complex, temporally dependent and synthetic-data contingent models. This is a crucial foundation for future work.
– Feature Ablation with Clinical Insights: We pivoted to implement feature ablation as a practical alternative, which has not been used before in previous work. This showcased an avenue towards model transparency that can be justified or questioned through clinical insights.

Deciding to extubate a patient from the ventilator can be a life-or-death decision. With the profound cost of an ill-informed decision, the need for reliable and interpretable assistive tools cannot be understated. Where the majority of previous work fails to recognise the gravity of the situation, our approach thrives by focusing on clinically informed data pre-processing, employing relevant architectures to capture temporal patient trajectories and model transparency. We intend for this study to be viewed as a robust platform to inspire future work to predict extubation failure, making those reading cognisant of the potential challenges and proposing means of addressing them, ultimately with the view of improving patient outcomes.
