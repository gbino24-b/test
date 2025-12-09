# Blockhouse Assessment

## Overview

1. *Task 1*: Forecast the spread defined as the difference between the last price and the index price for perpetual futures
2. *Task 2*: Forecast the funding rate at the next funding time


## Project Structure

```
.
├── dataProcessor.py              # Data loading and preprocessing
├── model.py                      # Model functionalities
├── spread_prediction.py          # Spread forecast implementation
├── funding_rate_prediction.py    # Funding rate forecast implementation
├── DATA/                         # Data directory (gzipped CSV files)
│   ├── LTC/
│   ├── ZORA/
│   └── ...
└── README.md
```

## Installation

```bash
pip install -r requirements.txt
```

## Usage

### Spread Prediction

The ticker can be defined at the start of the script. All model functionalities are contained within the model object. This object
contains two seperate functions for training and forecasting the data:

```
# Train the model
model.train_model()
# Execute the forecast
testing_segment['output'] = model.forecast()
```
To execute the forecast, simply run 'python spread_prediction.py' on your terminal


### Funding Rate Prediction

The ticker can be defined at the start of the script. All model functionalities are contained within the model object. This object
contains two seperate functions for training and forecasting the data:

```
# Train the model
model.train_model()
# Execute the forecast
testing_segment['output'] = model.forecast()
```
To execute the forecast, simply run 'python funding_rate_prediction.py' on your terminal

## Model Configuration

Default XGBoost parameters:
- `n_estimators`: 700
- `max_depth`: 3
- `learning_rate`: 0.01
- `subsample`: 0.9
- `colsample_bytree`: 0.9

### Hyperparameter Tuning

Optionally, there is a hyperparameter tuning function:

```
model.window_calibrate(window_size=window_size)
```

However, it can be slow depending on your window size

## Performance Metrics

The system evaluates predictions using Root Mean Square Error:

```
rmse = np.sqrt(np.mean((y_true - y_pred) ** 2))
```

## Requirements

See `requirements.txt` for full dependency list. Key dependencies:
- pandas
- numpy
- xgboost
- statsmodels
- matplotlib
- hurst
