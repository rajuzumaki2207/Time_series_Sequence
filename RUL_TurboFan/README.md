# Remaining useful life estimation for NASA Turbo Fan
This repo contains the notebooks on the NASA turbofan degradation dataset. The turbofan dataset consists of 4 separate challenges of increasing difficulty. The engines operate normally in the beginning but develop a fault over time. For each challenge, the engines in the train set are run to failure. The timeseries in the test set end 'sometime' before failure. The goal is to predict the Remaining Useful Life (RUL) of each turbofan engine in the test set. 
I have only attempted to predict the RUL for the first data set, the details of which are explained below.


<a href="https://drive.google.com/uc?export=view&id=15wzL-T7BGPO7yp4oQ4bOgeeq3MfcRKCc"><img src="https://drive.google.com/uc?export=view&id=15wzL-T7BGPO7yp4oQ4bOgeeq3MfcRKCc" style="width: 850px; max-width: 150%; height: auto" title="Click to enlarge picture"/>



  
  
  ## Methodology
  The question to ask is "Given these aircraft engine operation and failure events history, can we predict when an in-service engine will fail?" We re-formulate this       question into two closely relevant questions and answer them using two different types of machine learning models:
  
    -Regression models: How many more cycles an in-service engine will last before it fails?
    -Binary classification: Is this engine going to fail within w1 cycles?
  
  ## Data Summary
  
In the Dataset directory there are the training, test and ground truth datasets. The training data consists of multiple multivariate time series with "cycle" as the time unit, together with 21 sensor readings for each cycle. Each time series can be assumed as being generated from a different engine of the same type. The testing data has the same data schema as the training data. The only difference is that the data does not indicate when the failure occurs. Finally, the ground truth data provides the number of remaining working cycles for the engines in the testing data
 
  ## Results
  I have tried various techniques to calculate the RUL of the test data set and found that RNN based LSMT models showed the best results in capturing the ground truth.
  1. Basic Regression ![see code](https://github.com/rajuzumaki2207/Time_series_Sequence/blob/main/RUL_TurboFan/3_TurboFan_XGR_LGBMR.ipynb): 
  
  
  2. Distributed lag models: VAR models can handle multivariate timeseries, however the model initially creates lags of both our X and Y variables. Normally in timeseries the past values of Y play a large role in determining future values of Y. But since we assume our values for Y to be constant or linearly declining in the training set, incorporating these self-defined targets in the model and using them for prediction would highly influence model results and overemphasize the effect of Yt-1 on Yt. Distributed lag models gives us  a regression model where we have full control over how many lags we add for each variable.
  3. RNN based LSTMs: 
  

Reference:
- Saxena, A., Goebel, K., Simon, D., & Eklund, N. (2008). Damage propagation modeling for aircraft engine run-to-failure simulation. 2008 International Conference on Prognostics and Health Management. doi:10.1109/phm.2008.4711414

- Elattar, H. (n.d.). Intelligent information system to forecast the remaining life of aircraft turbofan engine.

- Riad, A. (n.d.). Evaluation of Neural Networks in the Subject of Prognostics As Compared To Linear Regression Model.

- Zhao, J., Xu, L., & Liu, L. (2007). Equipment Fault Forecasting Based on ARMA Model. 2007 International Conference on Mechatronics and Automation. doi:10.1109/icma.2007.4304129
Dataset can be found here [link](https://ti.arc.nasa.gov/tech/dash/groups/pcoe/prognostic-data-repository/)
