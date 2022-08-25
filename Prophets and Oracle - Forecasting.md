# Overview 
Forecasting and time series modeling depend on a fundamental assumption that the dependent variable's value depends on  past values of the time series. If this assumption does not hold, the time series approach is fundamentally flawed. Stock movements, asset prices, and consumer behaviors are oftentimes products of the macroeconomic environment and future expectations for that environment.

The second fundamental assumption of time-series models is a stationary environment. This means an absence of black swan events both positive and negative. This assumption usually holds when forecasting natural phenomenon, but breaks down when predicting human behavior. Any time-series model that may have radical shifts should include additional scenario planning. 

Keeping in mind these two fundamental limitations time-series modeling may be appropriate. Many modern time-series frameworks automate feature engineering, but these fundamentals are key when off-the-shelf approaches fail. 

## Time-Series Features 

### Lag Variables 
The most fundamental time-series feature is the auto-regressive or lag variable. An $AR(1)$ variable represents the time-period directly before the one we're forecasting. The $AR(1)$ model can be written as 

$$x_t = \alpha x_{t-1}+c+\epsilon_t$$
Where $x_t$ is the variable at time $t$, and $\alpha, c$ are parameters to be estimated. $\epsilon_t$ is the random error term. which is (often incorrectly) assumed to be normally distributed. The $AR(0)$ model represents white noise guided only by this error term. The auto-regressive model can handle higher-order terms, or lags for $p$ periods. This $AR(p)$ model is written as 

$$x_t = \sum_{n=1}^pa_nx_{t-n}+c+\epsilon_t$$
### Moving Average Variables
Moving averages are poorly named because they are not averages at all, rather they are lagged pervious error terms. A $MA(1)$ model is represented as
$$x_t=\theta\epsilon_{t-1}+c+\epsilon_t$$
As with the auto-regressive terms, the moving averages can be lagged for as many periods, $q$ as needed. The $MA(q)$ model is written as 
$$x_t = \sum_{m=1}^q\theta_m\epsilon_{t-m} + c + \epsilon_t$$
Auto-regressive components can be combined with moving-average components to create the $ARMA(p,q)$ model. 
$$x_t = \sum_{n=1}^pa_nx_{t-n}+\sum_{m=1}^q\theta_m\epsilon_{t-m}+c+\epsilon_t $$
$AR$, $MA$, and $ARMA$ models are not typically used in business, but provide good baselines to test more complicated models against. If prophet, deep neural networks, or SARIMAX models don't provide meaningful improvements to these simple models, then the time series task may be impossible. 

### ARIMA 
The auto-regressive integrated moving average model (ARIMA) is an ARMA model where moving averages are integrated through differenced variables. A differenced variable $d_t$ is simply $x_t-x_{t-1}$. ARIMA is specified by $(p, d, q)$ where $p$ is the number of autoregressive terms, $d$ is the number of differenced terms, and $q$ are lagged moving averages. 