# Walkthrough: Reproducing 5G Traffic Prediction for High-Density Events

This guide explains the implementation of the thesis project: **"Machine Learning Based Network Traffic Prediction for Improving 5G Reliability in High-Density Events."**

## 1. Project Overview
The objective is to predict cell-level traffic (throughput) in 5G networks during high-density events using a hybrid spatial-temporal approach.

### Key Modules:
- **LSTM (Long Short-Term Memory):** Captures temporal dependencies and baseline trends.
- **MH-STGCN (Multi-Head Spatial-Temporal Graph Convolutional Network):** Captures spatial correlations between neighboring cells (RUs).
- **GPR (Gaussian Process Regression):** Compensates for prediction residuals (errors) caused by stochastic network noise.
- **Fourier Decomposition:** Extracts periodic patterns from the raw signal to simplify the learning task.

## 2. Directory Structure
The implementation automatically manages the following directories:
- `results/graphs/`: Stores all publication-quality visualizations.
- `results/models/`: Stores trained PyTorch models (`.pth`).
- `results/metrics/`: Stores performance comparison tables (CSV).
- `results/predictions/`: Stores final prediction CSV files.

## 3. Data Processing Pipeline
1. **Aggregation:** UE-level data from `L5GHDD_Dataset` is aggregated into cell-level time series using RU Association mappings.
2. **Fourier Filtering:** The signal is decomposed into periodic and residual components.
3. **Augmentation:** A GAN-based framework (conceptually implemented) is used to synthesize rare high-traffic event patterns.
4. **Sliding Window:** Data is transformed into $[Batch, Window, Nodes]$ format for neural network consumption.

## 4. Model Training
The training loop handles:
- **Early Stopping:** To prevent overfitting.
- **Multi-Horizon Forecasting:** Predicting $t+1, t+2, ... t+h$.
- **Hybrid Fusion:** Combining the weighted outputs of LSTM and STGCN.

## 5. Evaluation
The models are compared against **ARIMA** and standalone **LSTM** using:
- **RMSE** (Root Mean Square Error)
- **MAE** (Mean Absolute Error)
- **MAPE** (Mean Absolute Percentage Error)
- **R² Score** (Coefficient of Determination)

---

### How to Run:
1. Open [Network_Traffic_Prediction_Thesis.ipynb](file:///e:/Research/Muttakin/Network_Traffic_Prediction_Thesis.ipynb) in Jupyter.
2. Ensure the `L5GHDD_Dataset` folder is in the same directory.
3. Run all cells. The results will be automatically populated in the `/results` folder.
