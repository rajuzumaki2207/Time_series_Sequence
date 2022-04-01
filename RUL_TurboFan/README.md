## Remaining useful life estimation for NASA Turbo Fan
This repo contains the notebooks on the NASA turbofan degradation dataset. The turbofan dataset consists of 4 separate challenges of increasing difficulty. The engines operate normally in the beginning but develop a fault over time. For each challenge, the engines in the train set are run to failure. The timeseries in the test set end 'sometime' before failure. The goal is to predict the Remaining Useful Life (RUL) of each turbofan engine in the test set. 
I have only attempted to predict the RUL for the first data set, the details of which are explained below.





Reference:
- Saxena, A., Goebel, K., Simon, D., & Eklund, N. (2008). Damage propagation modeling for aircraft engine run-to-failure simulation. 2008 International Conference on Prognostics and Health Management. doi:10.1109/phm.2008.4711414

- Elattar, H. (n.d.). Intelligent information system to forecast the remaining life of aircraft turbofan engine.

- Riad, A. (n.d.). Evaluation of Neural Networks in the Subject of Prognostics As Compared To Linear Regression Model.

- Zhao, J., Xu, L., & Liu, L. (2007). Equipment Fault Forecasting Based on ARMA Model. 2007 International Conference on Mechatronics and Automation. doi:10.1109/icma.2007.4304129
Dataset can be found here [link](https://ti.arc.nasa.gov/tech/dash/groups/pcoe/prognostic-data-repository/)
