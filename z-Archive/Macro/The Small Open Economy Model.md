The open economy IS curve is 

$$y_{t+1}=A-ar_t+bq_t$$
Where 
- $A$ is the level of autonomous demand
- $r$ is the real interest rate 
- $q$ is the log of the real exchange rate 

$$q = p^* + e- p$$
Where 
- $p^*$ is the log of the world price level
- $e$ is the log of the nominal exchange rate 
- $p$ is the log of the domestic price level

This is derived from the equation where the real exchange rate is 
$$q = e \cdot \frac {p^*}{p}$$
and the equation above can be produced by taking the log of both sides. Producers of differentiated goods in their home economy set their prices on the bases of domestic costs, and labour is the only input. A rise in e is a nominal depreciation. Real depreciation raises net exports. There is a one-period lag from both the interest rate and real exchange to output. 

Medium run equilibrium is 
$$y = \bar y, r = r^*$$
Therefore 
$$\begin{align}
\bar y &= A - ar^* + b\bar q \\
\bar q &= \frac 1 b(\bar y-A+ar^*)
\end{align}$$
An exogenous rise in equilibrium output, a fall in autonomous demand or a rise in the world real interest rate implies a depreciated real exchange rate in the new medium-run equilibrium. In addition the medium-run equilibrium is defined by a target inflation rate $\pi^T$. There is an additional assumption that the home's inflation target is equal to world inflation 

$$\pi^T=\pi^*$$
Under this assumption the central back would prefer a stable nominal exchange rate. If it choose a different inflation target then 

$$\begin{cases}
\pi^T > \pi^*, & \bar e \downarrow\\
\pi^T = \pi^*, & \bar e =\\
\pi^T < \pi^*, & \bar e \uparrow
\end{cases}
$$

If the home inflation rate is greater than the world's then the nominal exchange rate decreases. If the home inflation rate is less than the world inflation rate, then nominal exchange rate increases. This model assumes that the world inflation rate is constant. 

The flexible exchange rate small open economy has two related differences to the closed economy: 
1. The real interest rate is set by the is set by the exogenous world interest rate rather than domestic parameters like autonomous demand. The real exchange rate rather than the real interest rate varies in response to permanent aggregate demand and supply shocks. 
2. In dynamic adjustment of the economy to shocks, the central bank chooses the deviation of the home's real interest rate from the world rate. Output responses both to change in the interest rate and to the associated changes in the real exchange rate. 

Some assumptions remain from the closed economy model (C&S 2005)
1. The optimizing central bank uses rational expectations 
2. There is persistence in the inflation process, which means that the policy-maker faces a trade-off between inflation and the the output gam in the short-run
3. There is a policy lag from the central bank interest rate to decisions to output. 
4. There are agents in the forex market with rational expectations 

Assume that after a shock inflation moves away from its target level to $\pi_0 \neq \pi^*$. The central bank faces two problems 

First, If we assume that $\pi_0 > \pi^*$, the central bank has to work out the future optimal course of the deflation of output below and back up to its equilibrium level which will return inflation to $\pi^*$. i.e. it must chart the course $y_1, y_2, \dots, \bar y$. (Note that it cannot influence $y_0$ because there is a one period lag)

Second, The central bank in period 0 must set the interest rate $r_0$ to implement $y_t$. This is straightforward in the closed economy because the IS-curve is simply 
$$y_{t+1}=A-ar_t$$
So the optimal interest rate is 
$$r_0 = \frac{A-y_t}{a}$$
Unfortunately in the open-economy the IS-curve is
$$y_{t+1} = A-ar_t+bq_t$$
A change in the real interest rate will also affect output: an appreciation in response to the central bank's interest rate hike will decrease net exports and dampen output, thus reduces the required rise interest rate. 

The problem is broken down into the following 4 steps 
1. Find the sequence of output gaps along the path to equilibrium (using the PC and central bank loss function)
2. Assume that the rate at which interest rate deviation is reduced is the same as the rate of decline of the output gap on the path to equilibrium 
3. Given the equilibrium exchange rate, used the uncovered interest parity (UIP) condition to calculate the initial appreciation of the real exchange rate to $q_0$. 
4. Knowing $y_t$ from Step 1 and $q_0$ from Step 4, use the IS curve to work out the rise in home's interest rate above $r^*$ in period 0, and in general $r_t$ along the adjustment path 

**Step 1**: Begin with the PC and monetary rule equations. Under the assumption of domestic inflation targeting are the same as in the closed economy. 

$$PC: \pi_t = \pi_{t-1}+\alpha(y_t-\bar y)$$
The central bank is modeled as operating under discretion. It minimizes the loss function: 
$$L_t = (y_t-\bar y)^2 + \beta(\pi_t-\pi^T)^2$$
Where $\beta > 1$ means that the central bank places less weight on output fluctuations and $\beta < 1$ the central bank places less weight on inflation fluctuations. The central banks monetary rule comes from minimizing the loss function subject to the PC

$$MR: (y_t-\bar y) = -\alpha \beta(\pi_t-\pi^T)$$
This shows the relationship in period $t$ between inflation rate chosen indirectly and the level of output chosen directly in period $t-1$ to maximize its utility 

From the PC and MR we can derive the rate of deviations of inflation from target and output from equilibrium

$$\frac{\pi_{t-1}-\pi^T}{\pi_{t}-\pi^T} = \frac{1}{1+\alpha^2\beta} = \lambda = \frac{y_{t-1}-\bar y}{y_t-\bar y}$$
The proportionate rate of decline, $\lambda$ of the output gap depends only the PC and central bank's loss function, no open economy elements are involved.

**Steps 2 & 3** Assuming the central bank reduces the interest rate deviation linearly we can show that it does that at same rate as the output gap falls 

$$r_{t+1}-r^* = \lambda(r_t-r^*)$$
The cumulative interest gain rom holding home bonds during the adjustment process is 

$$\frac{r_0-r^*}{1-\lambda}$$

By the real UIP condition, this must be equal to expected real depreciation over the whole period of adjustment, implying 

$$QQ: \frac{r_0-r^*}{1-\lambda} = \bar q-q_0$$
What is the UIP condition? 

**Step 4** The central bank now uses the QQ equation, in the IS equation to sub for $q_0$ 

$$RX: y_t - \bar y = - \left[a+\frac{b}{1-\lambda} \right](r_{t-1}-r^*)$$
This equation implies that the central banks interest rate response to a shock depends on a parameters of the IS equation, the PC, and on the central banks preferences. 

$$RX: y_t - \bar y = - \left[a+b\left(1 +\frac{1}{\alpha^2\beta}\right) \right](r_{t-1}-r^*)$$
In graphical terms, higher $a,b$ flatten the slope of the RX curve in $r,y$ space: a desired output gap leads to a smaller interest rate response. 

For a given b, the more responsive is inflation to the output gap (higher $\alpha$) and the more averse to deviations of inflation is the central bank (higher $\beta$), the more the interest rate is raised above the world interest rate. 
