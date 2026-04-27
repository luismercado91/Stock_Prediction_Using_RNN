# RNN Stock Price Prediction

This project uses a Recurrent Neural Network (RNN) to predict future stock prices based on historical data. The model is trained on Apple (AAPL) closing price data and learns patterns from past time steps to estimate future values. This is a time-series forecasting problem where the model looks at a window of past data and predicts a value several steps ahead.

## Overview

- Uses historical stock data (AAPL)
- Builds sequences of past prices using a sliding window approach
- Trains an RNN model to predict future prices
- Evaluates performance using prediction error
- Visualizes actual vs predicted results

## How It Works

### Data Preparation
The dataset is loaded from a CSV file and processed using Pandas. The Date column is converted to a datetime format and sorted to ensure proper chronological order. Only the closing price is used for this model.

### Normalization
The data is scaled between 0 and 1 using MinMaxScaler. This is important for neural networks, especially RNNs, to ensure stable and efficient training.

### Sequence Creation
A sliding window approach is used to convert the data into sequences. Each training sample consists of a fixed number of past time steps used to predict a future value. In this case, the model uses 40 past days to predict the price 3 days ahead. The model effectively learns the mapping from past behavior to future outcomes.

### Train/Test Split
The dataset is split into training and testing sets. The model is trained only on past data and evaluated on unseen future data to simulate real-world prediction scenarios.

### Model Architecture
A SimpleRNN-based neural network is used. The model processes sequential data and learns temporal dependencies across time steps. While SimpleRNN is effective for demonstrating the concept, it has limitations compared to more advanced architectures like LSTM or GRU.

### Training
The model is trained over multiple epochs using batch processing. A portion of the training data is used for validation to monitor performance during training. Loss curves are used to track how well the model is learning.

### Prediction
After training, the model generates predictions on both training and test data. Since the model operates on normalized values, predictions are converted back to actual price values using the inverse transformation of the scaler.

### Evaluation
Predicted values are compared against actual values. Percentage error is calculated to quantify model performance. Visual plots are used to show how closely the predictions follow real stock price movements.

## Key Parameters

- time_steps = 40 (number of past days used as input)
- n = 3 (prediction horizon, predicts 3 days ahead)
- epochs = 50
- batch_size = 128

## Results

The model is able to capture general trends in stock price movement and produce reasonable future estimates. It performs better during stable periods and shows increased error during highly volatile market conditions. Visualization of actual vs predicted prices helps highlight both strengths and limitations of the model.

## Limitations

- Uses only closing price as input (no additional features like volume or indicators)
- SimpleRNN is limited in handling long-term dependencies compared to LSTM/GRU
- Stock prices are influenced by external factors not included in the model
- Not intended for real trading or financial decision-making

## Possible Improvements

- Replace SimpleRNN with LSTM or GRU for better performance
- Add additional input features such as volume, moving averages, or technical indicators
- Predict multiple future time steps instead of a single value
- Add dropout layers to reduce overfitting
- Compare results against baseline models to validate effectiveness

## Requirements

- Python 3.x
- NumPy
- Pandas
- Matplotlib
- Scikit-learn
- TensorFlow / Keras

Install dependencies using:
pip install numpy pandas matplotlib scikit-learn tensorflow

## How to Run

1. Place AAPL_hist_data.csv in the project directory  
2. Open RNN_Stock_Prediction.ipynb  
3. Run all cells in order  

## Notes

This project is focused on learning and understanding time-series modeling with RNNs. It is not a production-ready trading system. Some components such as feature engineering, robustness, and optimization are intentionally simplified.

## Author

Luis Mercado  
Firmware Engineer | Embedded Systems | Interested in AI/ML and real-world system behavior
