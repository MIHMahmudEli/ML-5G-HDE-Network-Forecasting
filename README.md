# Network Traffic Prediction for 5G Reliability in High-Density Events

## Overview

This project implements machine learning-based network traffic prediction models to improve 5G reliability in high-density events. The focus is on predicting cell-level aggregated throughput using various time series and spatial-temporal models.

## Dataset

**L5GHDD_Dataset (ACC Arena + Salt & Tar venues)**

- **Venues**: ACC Arena, Salt & Tar
- **Files/Structure**: 24 files per modality (500 UEs each → ~12,000 UEs total)
- **Modalities**: Throughput, PRB, SINR (DL+UL), BLER, RU_Association, Positions
- **Target Variable**: Cell-level (RU) aggregated throughput

## Models Implemented

1. **ARIMA** - Traditional statistical time series model
2. **LSTM** - Long Short-Term Memory neural network
3. **LSTM-GPR** - LSTM combined with Gaussian Process Regression
4. **Simplified STGCN** - Simplified Spatial-Temporal Graph Convolutional Network
5. **Hybrid (STGCN + LSTM-GPR)** - Ensemble of STGCN and LSTM-GPR

## Performance Metrics

| Model                  | RMSE       | MAE       | sMAPE    | R²       |
|------------------------|------------|-----------|----------|----------|
| ARIMA                 | 117.70    | 16.84    | 72.06   | -14.01  |
| LSTM                  | 25.20     | 13.59    | 66.36   | 0.31    |
| LSTM-GPR              | 25.80     | 14.07    | 61.69   | 0.28    |
| Simplified STGCN      | 29.00     | 15.64    | 70.05   | 0.09    |
| Hybrid (STGCN+LSTM-GPR) | 27.03   | 14.19    | 66.43   | 0.21    |

## Project Structure

```
Network_Traffic_Prediction_Colab.ipynb  # Main Jupyter notebook
Network_Traffic_Results/
├── graphs/                            # Generated visualization plots
├── metrics/
│   └── final_comparison.csv          # Model performance comparison
├── models/
│   ├── lstm_model.pt                 # Trained LSTM model
│   └── stgcn_model.pt                # Trained STGCN model
└── predictions/
    ├── arima_preds.npy               # ARIMA predictions
    ├── lstm_preds.npy                # LSTM predictions
    ├── lstm_gpr_preds.npy            # LSTM-GPR predictions
    ├── stgcn_preds.npy               # STGCN predictions
    ├── hybrid_preds.npy              # Hybrid model predictions
    └── final_hybrid_preds.csv        # Final hybrid predictions
```

## Approach

1. **Dataset Analysis & EDA**: Exploratory data analysis and visualization
2. **Problem Formulation**: Define prediction task and preprocessing
3. **Baseline Models**: ARIMA and basic LSTM implementation
4. **Advanced Models**: LSTM-GPR, Simplified STGCN, and Hybrid approaches
5. **Optimization**: Hyperparameter tuning and model refinement
6. **Final Evaluation**: Comprehensive comparison and analysis

## Requirements

- Python 3.x
- Jupyter Notebook
- Required libraries: pandas, numpy, matplotlib, seaborn, scikit-learn, tensorflow/pytorch, etc. (see notebook for full list)

## Usage

1. Open `Network_Traffic_Prediction_Colab.ipynb` in Jupyter Notebook or Google Colab
2. Run cells sequentially from top to bottom
3. All outputs and results will be saved to the `Network_Traffic_Results/` directory

## Key Findings

- LSTM-based models significantly outperform traditional ARIMA
- Spatial-temporal models like STGCN capture network topology effectively
- Hybrid approaches provide balanced performance across metrics
- Best performing model: LSTM (highest R² = 0.31)

## Notes

- This notebook was designed for Google Colab but can run locally
- All model outputs are pre-computed and saved in the results directory
- For detailed implementation, refer to the notebook cells and comments

## Contact

For questions or contributions, please refer to the notebook documentation or contact the project maintainer.