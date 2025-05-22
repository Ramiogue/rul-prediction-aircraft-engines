# Remaining Useful Life (RUL) Prediction for Aircraft Engines

---

## Executive Summary

This project focuses on predicting the Remaining Useful Life (RUL) of aircraft engines using NASA’s CMAPSS dataset. RUL estimation is crucial for predictive maintenance, enabling industries to detect early signs of failure, optimize maintenance schedules, and avoid costly breakdowns.

We implemented and compared three models:
- LightGBM (gradient boosting)
- Support Vector Regression (SVR)
- LSTM (deep learning, sequence-based)

All results are visualized using an interactive Power BI dashboard.

---

## Why This Project Matters

In real-world applications like aviation and manufacturing, machinery failure can lead to:

- Safety hazards  
- Operational downtime  
- High repair costs

Predictive maintenance using RUL prediction ensures:
- Machines are serviced before failure  
- Operations remain safe and efficient  
- Maintenance is data-driven and not reactive

This project simulates that process using a real-world industrial dataset and provides both predictive models and business-ready visualizations.

---

## Project Files and Execution

All required files are included in this repository for full reproducibility.

### Included:
- `train_FD001.txt` – Data used for training and testing  
- `model_comparison.csv`, `actual_vs_predicted.csv` – Model results  
- `RUL_prediction_dashboard.pbix` – Power BI dashboard  
- [Google Colab Notebook](https://colab.research.google.com/drive/1XGoNXBWzPctH-voNaeWPXreqB_pvBA5h#scrollTo=S2vPqmMW1ng5) – End-to-end execution

---

## Dataset: NASA CMAPSS

- 100+ simulated engines, each running to failure  
- 21 sensors, 3 operational settings  
- Target: Remaining Useful Life (RUL)

Source:  
[NASA Prognostics Data Repository – CMAPSS](https://www.nasa.gov/content/prognostics-center-of-excellence-data-set-repository)

---

## Objective

Build ML models that estimate RUL using time-series sensor data and engineered features.  
Evaluate performance with:
- MAE (Mean Absolute Error)  
- RMSE (Root Mean Squared Error)  
- R² (Goodness of Fit)

---

## Feature Engineering

- Rolling means (window=5)  
- Rolling standard deviation  
- Delta (cycle-to-cycle difference)  
- EMA (Exponential Moving Average)  
- Cycle normalization

These features help models capture temporal degradation trends critical for accurate RUL estimation.

---

## Model Selection Rationale

This project compares three model types to learn from both tabular structure and time-dependent behavior in the dataset:

- LightGBM  
  Chosen for its performance and efficiency on tabular data. It handles feature interactions well and offers fast training and strong generalization. Best suited for structured datasets with engineered features.

- Support Vector Regression (SVR)  
  Selected as a baseline nonlinear model. SVR with an RBF kernel provides robustness in capturing complex relationships without requiring deep architectures. It serves as a middle ground between tree models and neural networks.

- LSTM (Long Short-Term Memory)  
  Chosen to directly model temporal dependencies. LSTM networks are known for handling sequence data and remembering long-term patterns critical for modeling degradation. Although it underperformed here, it highlights the complexity of time-series generalization with small datasets.

---

## Results Summary

### Validation and Holdout Metrics

| Model     | Dataset     | MAE        | RMSE      | R²          |
|-----------|-------------|------------|-----------|-------------|
| LightGBM  | Validation  | 14.586393  | 21.080658 | 0.90926767  |
| LightGBM  | Holdout     | 14.391989  | 20.632263 | 0.90706212  |
| SVM       | Validation  | 17.714910  | 27.635183 |  0.8440740  |
| SVM       | Holdout     | 17.409732  | 26.362914 | 0.84826498  |
| LSTM      | Holdout     | 55.848114  | 67.724222 | -0.00029802 |

See: `model_comparison.csv` and `actual_vs_predicted.csv`

---

## Power BI Dashboard

The dashboard presents:

| Page | Title                         | Highlights                                |
|------|-------------------------------|-------------------------------------------|
| 1    | Project Overview              | Goal, data summary, sensor trends         |
| 2    | Model Performance Summary     | MAE, RMSE, R² for all models              |
| 3    | Actual vs Predicted RUL       | Scatter plots: true vs predicted RUL      |
| 4    | Sensor Insights               | Interactive engine and sensor trends      |

File: `RUL_prediction_dashboard.pbix`

---

## Scientific References

This project builds on recent research in prognostics and health management:

1. Babu et al. (2016) – CNN for RUL estimation  
   Expert Systems with Applications  
   [https://doi.org/10.1016/j.eswa.2016.09.014](https://doi.org/10.1016/j.eswa.2016.09.014)

2. Zheng et al. (2017) – LSTM for Remaining Useful Life  
   IEEE Transactions on Industrial Electronics  
   [https://doi.org/10.1109/TIE.2017.2715283](https://doi.org/10.1109/TIE.2017.2715283)

3. Li et al. (2019) – Multi-scale feature extraction for RUL  
   Reliability Engineering & System Safety  
   [https://doi.org/10.1016/j.ress.2019.106554](https://doi.org/10.1016/j.ress.2019.106554)

4. Zhang et al. (2019) – Feature engineering and uncertainty quantification for RUL  
   Mechanical Systems and Signal Processing  
   [https://doi.org/10.1016/j.ymssp.2019.106587](https://doi.org/10.1016/j.ymssp.2019.106587)

5. Saxena & Goebel (2008) – CMAPSS dataset paper  
   [NASA Dataset Link](https://www.nasa.gov/content/prognostics-center-of-excellence-data-set-repository)

---

## Tech Stack

- Python: Pandas, Scikit-learn, LightGBM, PyTorch  
- Power BI: Visual storytelling  
- Google Colab: Notebook-based execution  
- Joblib: Model persistence  
- Git and GitHub: Version control and collaboration

---

## Acknowledgements

This project was completed with the help of:

- NASA Prognostics Data Repository  
- Open-source ML tools: LightGBM, Scikit-learn, PyTorch  
- Google Colab and Power BI Desktop  
- ChatGPT by OpenAI, used for:
  - Structuring and debugging Python scripts  
  - Designing the evaluation pipeline  
  - Creating documentation and model insights

---

## Author

**Name**: Tshepang Ramaoka  
**Email**: ramaokafelicia@gmail.com

---

