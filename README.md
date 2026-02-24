# Development of a Neural Network to Predict a Star’s Absolute Surface Temperature

## 📋 About the Project
Study of the “Sky at Your Fingertips” observatory dataset. Development of a neural network model that can predict the surface temperature of observed stars.

### 🎯 Problem Statement
* Build a neural network that predicts the absolute surface temperature of a star.

**Research objectives:**
* Analyze the “Sky at Your Fingertips” observatory data,
* Explore relationships between available features and prepare the data for predictive neural networks (baseline and with hyperparameters),
* Develop a neural network that predicts the absolute surface temperature of a star,
* Provide recommendations to the observatory: conclusions and additional suggestions based on comparing two models.

### 📊 Data
The study uses characteristics of 240 previously studied stars from the observatory database. The dataset contains the following features:
- `L/Lo` — relative luminosity (star luminosity relative to the Sun),
- `R/Ro` — relative radius (star radius relative to the Sun’s radius),
- `Mv` — absolute stellar magnitude (a physical quantity describing star brightness),
- Star color (`white, red, blue, yellow, yellow-orange`, etc.) — determined via spectral analysis,
- Star type: from `Brown Dwarf` to `Hypergiant`,
- `T(K)` — absolute temperature in Kelvin (star surface temperature in K).

### 🤖 Prediction Models
Neural networks based on the following technologies: tensorflow, torch, Sequential, Adam.

### 📈 Results
Training and comparison of neural networks.

**Results by model type:**
* **Baseline model** (simple neural network without hyperparameter tuning):
  - Architecture: MLP (Tanh, ReLU, Linear), training on a standardized target with inverse transform back to Kelvin.
  - From the Actual–Prediction plot, the model generally captures the temperature scale but makes noticeable errors on extremely hot stars.
  - Quality: RMSE = 4778 K, MAE was about 2790 K.

* **Improved model** with the same architecture and a grid search over dropout and batch_size:
  - The architecture was unchanged; only hyperparameters were tuned: dropout and batch_size.
  - Best result: dropout = 0.0, batch_size = 64.
  - Quality: RMSE = 4212 K (meets the requirement ≤ 4500).

### 🎯 Key Conclusions
* The improved model performs better: RMSE decreased from 4778 to 4212 K, which is roughly a 12% improvement.
* The search showed that dropout does not help for this task: the best result is achieved with dropout = 0.0. With such a small dataset and this architecture, dropout likely reduces model capacity more than it prevents overfitting.
* Increasing batch_size to 64 produced the most stable training and the best result.

### 🛠️ Tech Stack
**Data analysis:** pandas, numpy, scipy  
**Visualization:** matplotlib, seaborn  
**Machine learning:** tensorflow, torch, Sequential, Adam  
**Model explainability:** SHAP  
**Statistics:** statsmodels, phik  
**Notebooks:** Jupyter Notebook  

## 🔄 Latest Model Improvements
- Hyperparameters were optimized
