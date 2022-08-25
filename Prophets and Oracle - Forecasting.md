# Overview 
Forecasting and time series modeling depend on a fundamental assumption that the dependent variable's value depends on  past values of the time series. If this assumption does not hold, the time series approach is fundamentally flawed. Stock movements, asset prices, and consumer behaviors are oftentimes products of the macroeconomic environment and future expectations for that environment.

The second fundamental assumption of time-series models is a stationary environment. This means an absence of black swan events both positive and negative. This assumption usually holds when forecasting natural phenomenon, but breaks down when predicting human behavior. Any time-series model that may have radical shifts should include additional scenario planning. 

Keeping in mind these two fundamental limitations time-series modeling may be appropriate. Many modern time-series frameworks automate feature engineering ^[[A Deep Dive on ARIMA Models. From white noise to SARIMAX and beyond | by Matt Sosna | Towards Data Science](https://towardsdatascience.com/a-deep-dive-on-arima-models-8900c199ccf)], but these fundamentals are key when off-the-shelf approaches fail. 

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

$$d_t = \sum_{n=1}^pa_nd_{t-n}+\sum_{m=1}^q\theta_m\epsilon_{t-m}+c+\epsilon_t $$

### SARIMA 
SARIMA adds a seasonality component to ARIMA. This additional seasonality is specified by an offset number of lags, $s$ and $p_s, d_s, q_s$ which specify the auto-regressive, differenced, and moving-average components of the seasonality. 

$$d_t = \sum_{n=1}^pa_nd_{t-n}+\sum_{n=1}^q\theta_n\epsilon_{t-m} + \sum_{n=1}^{p_s}\phi_n d_{t-sn}+\sum_{n=1}^{q_s}\eta_n\epsilon_{t-sn} + c + \epsilon_t$$
### SARIMAX 
Adding exogenous variables, $z_1, ..., z_2$ to our model is quite simple. It simply involves an extra set of terms to handle variables that could affect our forecast outside of the signal within the time-series itself. For future terms exogenous variables often have to be specified or predicted. This will create errors in your exogenous forecasts that propagate to your final model. Limit the number of predicted exogenous variables in the model to maintain parsimony. 

$$d_t = \sum_{n=1}^pa_nd_{t-n}+\sum_{n=1}^q\theta_n\epsilon_{t-m} + \sum_{n=1}^{p_s}\phi_n d_{t-sn}+\sum_{n=1}^{q_s}\eta_n\epsilon_{t-sn} + \sum_{n=1}^r\beta_rz_r+ c + \epsilon_t$$

SARIMAX is hyper parameterized by $(p,d,q)(p_s,d_s,q_s)(s)$ and any additional exogenous variables. Using large orders for these numbers should be done with caution because model dimensionality can explode leading to overfitting. 

# Nonlinear Modeling

All the models above are linear in nature and can be estimated using standard OLS. statsmodels ^[[Introduction — statsmodels](https://www.statsmodels.org/stable/index.html)]. Standard regression techniques can be applied to these models. Moving beyond SARIMAX should be done with carefully and only with good reason. More often than not is SARIMAX models are not providing desired results the premise of the task should be revisited. Despite thi

## UCM

## Prophet

