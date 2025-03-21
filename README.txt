Estimation of CO₂ Emissions in Fault Systems at a Global Scale
=============================================================

This repository contains a structured workflow and dataset for estimating CO₂ emissions in fault systems on a global scale, integrating geophysical, geological, tectonic, and environmental variables. It provides a Machine Learning approach, accompanied by interpretability techniques and geostatistical methods, to generate a global CO₂ degassing map.

Table of Contents
-----------------
1. Project Description
2. Key Features
3. Repository Structure
4. Setup and Installation
5. Usage
6. Methodology and Models
7. Results Overview
8. Contributing
9. Contact

1. Project Description
----------------------
- Title: Estimation of CO₂ Emissions in Fault Systems at a Global Scale
- Authors: Rolando Betancourt¹, and Carlos Vargas¹
  ¹Department of Geosciences, Universidad Nacional de Colombia, Bogotá, Colombia
- Corresponding Authors:
  - Rolando Betancourt: rbetancourt@unal.edu.co
  - Carlos Vargas: cavargasj@unal.edu.co

Abstract
~~~~~~~~
This repository focuses on quantifying CO₂ fluxes in fault systems worldwide. The emission of carbon dioxide (CO₂) in fault systems is regulated by tectonic, geophysical, geological, and environmental factors. We compiled 868 degassing records and used multiple Machine Learning algorithms (Support Vector Regression, K-Nearest Neighbors, Decision Tree, Random Forest, Gradient Boosting, and an ensemble Stacking Regressor) to predict CO₂ fluxes. Our best model achieved an R² of 0.678 in testing, surpassing individual models. We further extended our spatial coverage by applying Empirical Bayesian Kriging (EBK) on the predictions from the Tamburello et al. (2018) dataset. This approach yielded a comprehensive CO₂ degassing map, underscoring the significance of both tectonic and environmental variables in explaining CO₂ emissions.

2. Key Features
---------------
1. Global-Scale Database
   - A collection of 868 degassing records drawn from 37 bibliographic sources.
   - Covers diverse tectonic environments and volcanic to non-volcanic settings.

2. Multiple Explanatory Variables
   - Geophysical (heat flow, Bouguer anomaly, peak ground acceleration)
   - Tectonic (distance to faults, proximity to volcanoes)
   - Geological (lithology, porosity, permeability)
   - Environmental (soil pH, annual mean temperature, CO₂ atmospheric concentration)

3. Robust Machine Learning Pipeline
   - Five individual algorithms (SVR, KNN, Decision Tree, Random Forest, Gradient Boosting)
   - Stacking Regressor meta-model, which integrates all base learners
   - Automated hyperparameter tuning using GridSearchCV / RandomizedSearchCV

4. Interpretability and Visualization
   - Permutation Importance, Partial Dependence Plots (PDP), and SHAP analysis
   - Learning Curves for each algorithm
   - CO₂ emissions map generation via Empirical Bayesian Kriging

5. Scalable and Reproducible
   - Clear data preprocessing steps, environment setup, and model training notebooks
   - Results and figures saved automatically for quick review

3. Repository Structure
-----------------------
.
├── CO2_Flux_Analysis_and_Modeling.ipynb   # Main Jupyter Notebook
├── data/
│   ├── CO2_Flux_model_new.csv            # Compiled dataset
│   ├── CO2_Flux_model_Tamburello_new.csv                       
│   └── ...
├── figures/
│   ├── histogram_flux.png
│   ├── ...                               # Images generated from notebooks
│   └── ...
├── LICENSE                               
├── README.md                             # Project README
├── requirements.txt                      # Python libraries required
└── ...

4. Setup and Installation
-------------------------
1. Clone the repository:

   git clone https://github.com/YourUsername/GlobalFaultCO2Flux.git

2. Install dependencies
   - Use pip

     pip install -r requirements.txt

3. Jupyter Notebook / Lab
   - Open and run CO2_Flux_Analysis_and_Modeling.ipynb to explore data preprocessing,
     model training, and result visualization.

5. Usage
--------
1. Data Preprocessing
   - Missing values are handled by median imputation.
   - Right-skewed CO₂ flux values undergo a log transformation for stable model training.
   - Inverse distance transformations emphasize proximity to faults, mineralized zones, and volcanoes.

2. Model Training
   - Run the notebook sections to reproduce cross-validation, hyperparameter tuning, and final model evaluation.
   - Evaluate model metrics (R², MSE, MAE) on both validation and test splits.

3. Interpretability
   - Permutation Importance and SHAP plots in the notebook clarify how each variable influences CO₂ flux predictions.
   - Partial Dependence Plots show how a single feature (e.g., Heat Flow) affects predicted CO₂ flux.

4. Map Generation
   - The final Stacking Regressor’s predictions feed into an Empirical Bayesian Kriging procedure to generate a global degassing map.

6. Methodology and Models
-------------------------
- Data Split: 70% training, 15% validation, 15% test.
- Algorithms:
  1. Support Vector Regression (SVR)
  2. K-Nearest Neighbors (KNN)
  3. Decision Tree
  4. Random Forest
  5. Gradient Boosting
  6. Stacking Regressor (meta-learner: XGBRegressor)

- Key Steps:
  1. Feature engineering (inverting distances, log transform for flux)
  2. GridSearchCV / RandomizedSearchCV for hyperparameter tuning
  3. Ensemble approach through Stacking Regressor
  4. Kriging-based interpolation for final global map

7. Results Overview
-------------------
- Performance:
  - The Stacking Regressor outperformed individual models, achieving an R² of 0.678 on the test set.
  - The best single models were Random Forest (R² ≈ 0.646) and Gradient Boosting (R² ≈ 0.638).

- Interpretability:
  - Bouguer anomaly, PGA, annual mean temperature, CO₂ molar fraction, heat flow, distance to faults,
    and porosity emerged as major predictors.
  - SHAP plots revealed nuanced relationships between these variables and CO₂ flux.

- Application:
  - Applied to the Tamburello et al. (2018) dataset, expanding spatial coverage.
  - Combined with Empirical Bayesian Kriging to produce a global CO₂ degassing map, highlighting active volcanic and tectonic regions as prominent emission zones.

8. Contributing
---------------
1. Fork this repository.
2. Create a feature branch: git checkout -b feature/NewInsights
3. Commit your changes: git commit -m 'Add new geophysical dataset'
4. Push to the branch: git push origin feature/NewInsights
5. Open a Pull Request: We will review your proposals.

We welcome suggestions to improve data coverage, modeling strategies, or interpretability techniques.

9. Contact
-----------
For questions, collaboration, or more information:

- Rolando Betancourt – rbetancourt@unal.edu.co
- Carlos Vargas – cavargasj@unal.edu.co

Department of Geosciences, Universidad Nacional de Colombia, Bogotá, Colombia

Acknowledgments
---------------
- Thanks to all bibliographic sources referenced in the paper for providing the raw CO₂ degassing measurements.
- We appreciate the valuable input of the research community in refining Machine Learning-based approaches to geological emission studies.

Disclaimer
----------
This project is provided “as is” without any warranties or guarantees. It is intended for academic and research purposes. Use at your own discretion and risk.

https://doi.org/10.5281/zenodo.15066291
