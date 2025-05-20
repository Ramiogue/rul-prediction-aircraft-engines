#  Remaining Useful Life (RUL) Prediction for Aircraft Engines

---

## Executive Summary

This project focuses on predicting the Remaining Useful Life (RUL) of aircraft engines using NASA’s CMAPSS dataset. RUL estimation is crucial for predictive maintenance, enabling industries to detect early signs of failure, optimize maintenance schedules, and avoid costly breakdowns.

We implemented and compared three models:
- **LightGBM** (gradient boosting)
- **Support Vector Regression (SVR)**
- **LSTM** (deep learning, sequence-based)

All results are visualized using an interactive **Power BI dashboard**.

---

##  Why This Project Matters

In real-world applications like aviation and manufacturing, machinery failure can lead to:

- Safety hazards  
- Operational downtime  
- High repair costs

**Predictive maintenance** using RUL prediction ensures:
- Machines are serviced **before** failure  
- Operations remain **safe and efficient**  
- Maintenance is **data-driven** and not reactive

This project simulates that process using a real-world industrial dataset and provides both predictive models and business-ready visualizations.

---

## Project Files & Execution

All required files are included in this repository for full reproducibility.

### Included:
- `data.txt` → data used for training and testing   
- `RUL_prediction_dashboard.pbix` → Power BI dashboard
- **Google Colab Notebook**: End-to-end execution and output generation  
    

---

## Dataset: NASA CMAPSS

- 100+ simulated engines, each running to failure  
- 21 sensors, 3 operational settings  
- Target: Remaining Useful Life (RUL)

**Source**:  
[NASA Prognostics Data Repository – CMAPSS](https://www.nasa.gov/content/prognostics-center-of-excellence-data-set-repository)

---

## Objective

Build ML models that estimate RUL using time-series sensor data and engineered features.  
Evaluate performance with:
- **MAE** (Mean Absolute Error)  
- **RMSE** (Root Mean Squared Error)  
- **R²** (Goodness of Fit)

---

## Models and Features

### Features:
- Rolling means (`window=5`)  
- Rolling std deviation  
- Delta (cycle-to-cycle difference)  
- EMA (Exponential Moving Average)  
- Cycle normalization  

### Models:
- **LightGBM**: Tree-based, tabular-friendly, interpretable  
- **SVR**: Kernel-based, non-linear regression  
- **LSTM**: Sequence model for time-series degradation learning

---

##  Results Summary

### Validation & Holdout Metrics

| Model     | Dataset     | MAE   | RMSE  | R²     |
|-----------|-------------|--------|--------|--------|
| LightGBM  | Validation  | 14.59  | 21.08 | 0.91   |
| LightGBM  | Holdout     | 14.39  | 20.63 | 0.91   |
| SVM       | Validation  | 17.71  | 27.64 | 0.84   |
| SVM       | Holdout     | 17.41  | 26.36 | 0.85   |
| LSTM      | Holdout     | 55.86  | 67.72 | -0.00  |

 See: `model_comparison.csv` and `actual_vs_predicted.csv`

---

## Power BI Dashboard

The dashboard presents:

| Page | Title                         | Highlights                                |
|------|-------------------------------|-------------------------------------------|
| 1    | Project Overview              | Goal, data summary, sensor trends         |
| 2    | Model Performance Summary     | MAE, RMSE, R² for all models              |
| 3    | Actual vs Predicted RUL       | Scatter plots: true vs predicted RUL      |
| 4    | Sensor Insights               | Interactive engine + sensor trends        |

File: `RUL_prediction_dashboard.pbix`

---

## Scientific References

This project builds on recent research in prognostics and health management:

1. **Babu et al. (2016)** – CNN for RUL estimation  
   _Expert Systems with Applications_  
   [https://doi.org/10.1016/j.eswa.2016.09.014](https://doi.org/10.1016/j.eswa.2016.09.014)

2. **Zheng et al. (2017)** – LSTM for Remaining Useful Life  
   _IEEE Transactions on Industrial Electronics_  
   [https://doi.org/10.1109/TIE.2017.2715283](https://doi.org/10.1109/TIE.2017.2715283)

3. **Li et al. (2019)** – Multi-scale feature extraction for RUL  
   _Reliability Engineering & System Safety_  
   [https://doi.org/10.1016/j.ress.2019.106554](https://doi.org/10.1016/j.ress.2019.106554)

4. **Saxena & Goebel (2008)** – CMAPSS dataset paper  
   [NASA Dataset Link](https://www.nasa.gov/content/prognostics-center-of-excellence-data-set-repository)

---

## Tech Stack

- **Python**: Pandas, Scikit-learn, LightGBM, PyTorch  
- **Power BI**: Visual storytelling  
- **Jupyter Notebook + Colab**: All-in-one execution  
- **Joblib**: Model saving/loading  
- **Git & GitHub**: Version control
  
---

## Acknowledgements

This project was completed with the help of:

- **NASA Prognostics Data Repository**  
- **Open-source ML tools**: LightGBM, Scikit-learn, PyTorch  
- **Google Colab** and **Power BI Desktop**  
- **ChatGPT by OpenAI**, used for:
  - Structuring and debugging Python scripts  
  - Designing the evaluation pipeline  
  - Creating documentation

---

