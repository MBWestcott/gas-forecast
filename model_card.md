# Model Card for UK natural gas system price prediction using random forest

## Model Description

**Input:** 

The model's input is details of a day's operation of the UK National Gas Transmission system.

The data is downloaded from https://data.nationalgas.com/ and consists of the following data items:
Aggregate LNG Importations - Daily Flow\
Beach and IOG - Beach Delivery\
Beach and IOG - Daily Flow\
Beach Including Norway - Daily Flow\
Interconnector - Daily Flow\
Interconnector - Delivery\
Storage - Daily Flow\
Storage - Delivery\
Demand Actual, NTS, D+1\
SAP, 30 day rolling average\
SAP, 7 Day rolling average\
SAP, Actual Day\
SMP Buy, Actual Day\
SMP Sell, Actual Day\
System Entry Flows, National, Forecast\
Demand Forecast, NTS, hourly update\
Predicted Closing Linepack (PCLP1)\
Composite Weather Variable - Actual\
LNG Stock Level\
Long Storage - Actual Stock\
Long Storage - Stock Level at Max Flow\
Medium Storage - Actual Stock\
Medium Storage - Stock Level at Max Flow\
Short Storage - Actual Stock\
Short Storage - Stock Level at Max Flow\
Storage, Long Range, Average flow (7 days)\
Storage, Long Range, Maximum potential flow\
Storage, Long Range, Stock Levels\
Storage, Medium Range, Average flow (7 days)\
Storage, Medium Range, Maximum potential flow\
Storage, Medium Range, Stock Levels\
Storage, Short Range, Average flow (7 days)\
Storage, Short Range, Maximum potential flow\
Storage, Short Range, Stock Levels\
System Entry Flows, National, Physical\
Demand - Cold\
Demand - Cold, (excluding interconnector and storage)\
Demand - Warm\
Demand - Warm, (excluding interconnector and storage)\
Demand, NTS, SND\
Demand, NTS, SND, (excluding interconnector and storage)\
Composite Weather Variable - Cold\
Composite Weather Variable - Normal\
Composite Weather Variable - Warm\

**Output:**

The model's output is a prediction of the following day's System Average Price, System Marginal Price (Buy) and System Marginal Price (Sell) for the UK national gas transmission system.

The System Average Price (SAP) is the volume weighted average price of trades on the UK natural gas On-the-Day Commodity Market - i.e. gas for immediate delivery.\
The System Marginal Price (Buy) (SMPBuy) is related to the day's highest price, and is the price that suppliers must pay for the balance of gas used by their customers, if that is more than the amount they have supplied to the system (a "short imbalance")\
The System Marginal Price (Sell) (SMPSell) is related to the day's lowest price, and is the price that suppliers receive for any surplus gas that they have supplied to the system, which their customers have not used (a "long imbalance").\
All prices are in pence per kilowatt-hour (p/kWh).

**Model Architecture:** 

The model consists of three sklearn Random Forest regressors: one for each of the price targets. Random Forest was selected as the best performing model type out of a shortlist that comprised: linear regression; random forest; gradient boosting; a Long Short-Term Memory (LSTM) Recurrent Neural Network; and a residual model LSTM RNN. Although the Random Forest regressors were the best machine learning models based on RMSE, they still did not outperform a naive prediction which assumes that the next day's price will be the same as the current day's price, for any of the three price targets.

The dataset used to train, validate and test the model covered the start of April 2021 (roughly coinciding with the easing of most Covid restrictions in the UK, which would have affected gas usage patterns) until the current month of April 2025. The earliest 70% was used to train all candidate models, with the next 20% by date being used as a validation set for model selection, as well as for hyperparameter tuning for the Random Forest regressors that emerged as best. The latest 10% was then used to show the performance of the final tuned regressors.



## Performance

When tested against the latest 10% of the data (covering 24th November 2024 to 19th April 2025) these were the Root Mean Squared Errors of the predictions for each price label, and for comparison, the RMSE for the naive predictions (tomorrow's price = today's price). The naive predictions were slightly better (lower RMSE) in all cases.

| Price  | Model RMSE   | Naive RMSE    |
|--------|--------------|---------------|
| SAP    | 0.2355       | 0.2208        |
| SMPBuy | 0.2417       | 0.2348        |
| SMPSell| 0.2455       | 0.2298        |


![UK natural gas system price predictions using random forest - model RMSE v naive RMSE](test_rmses.png)

## Limitations

None of the three price prediction models outperforms (measured by RMSE) a naive prediction which assumes that the next day's price will be the same as the current day's price. The prediction is restriced to the next day's price, no later.

## Trade-offs

The model is biased against predicting large price movements (more than 50% higher or lower than the current day's price), and zero prices. These instances, representing 2.2% of the dataset, were excluded from training, test and validation.
