# Game Theory Week 1 
Ayush Kumar
October 20, 2022

## Problem 1 

1. First Grid
$BR_1(L) = B$ 
$BR_1(R) = T$ 

$BR_2(T) = R$
$BR_2(B) = L$

$$NE = (B,T) \text{  or } (R, L) $$

2. Second Grid
$$BR_1(L) = M, BR_1(C) = T, BR_1(R) = B$$
$$BR_2(T) = L, BR_2(M) = C, BR_2(B) = R$$
$$NE = (R, B)$$

3. Third Grid 
```math
BR_1(x) = 
\begin{cases}
x = L, & T \\
x = C, & T \\
x = R, & B
\end{cases}

\qquad 

BR_2(y) = \begin{cases} 
y= T, & L \text{ or } C \\
y=B,  & R
\end{cases}
```
Therefore there are three distinct Nash equilibria: 

$$NE = (T, L), (T,C), (B,R)$$

## Problem 2 

1. For player one to have a dominant strategy $T$ she must have no better alternative for any of player two's actions. Therefore 

$$a > c \text{ and }b>d$$

2. There is no pure-strategy equilibrium if neither player has a dominant strategy. One possible game like this is where 

```math
\begin{cases} a > c, \\d > b,\\ \gamma > \alpha, \\\beta > \delta \end{cases}
```

If I model the best-response functions with these assumptions we arrive at 
$$BR_1 = \begin{cases}
r_2 = L, & T \\
r_2 = R, & B
\end{cases}$$
$$BR_2 = \begin{cases}
r_1 = T, & R \\
r_1 = B, & L
\end{cases}$$
Here there is no pure-strategy Nash Equilibrium because there is no situation in which $r_1^* = B(r_2^*)$ and vice versa. 

3. Assuming player 1 has a mixed strategy probability profile of $(T: p, B: 1-p)$ and player 2 has a mixed strategy probability profile of $(L: q, R: 1-q)$. 

We begin by modeling the payoffs as expected values

$$U_1 = 
\begin{cases}
T, & aq+b(1-q) \\
B, & cq+d(1-q)
\end{cases}$$
$$U_2 = 
\begin{cases}
L, & \alpha p+\beta(1-p) \\
R, & \gamma p+\delta(1-p)
\end{cases}$$
If we assume that player 1 will randomize if both $T$ and $B$ are equal then we can find the probability $q$ by setting these terms equal to one another. 

$$aq + b(1-q) = cq+d(1-q)$$
$$aq-cq = d(1-q) - b(1-q)$$
$$aq-cq+dq-bq = d-b$$
$$q = \frac{d-b}{a-c+d-b}$$
We can do the same to find the probability p based on player 2's payoff functions 

$$\alpha p +\beta(1-p)=\gamma p+\delta(1-p)$$
$$\alpha p - \beta p - \gamma p + \delta p = \delta - \beta$$
$$p = \frac{\delta-\beta}{\alpha-\beta-\gamma+\delta}$$
The players would use these probabilities to pick their outcomes in a mixed-strategy Nash equilibrium. 
4. The only time this game does not have a pure-strategy Nash equilibrium is when the two players' best-response functions are at odds with each other. This can only happen in two ways. The first is shown in part (2) the second is by inverting both outcomes, but the result is the same. When this happens, the players will play the game based on a mixed strategy. Player 1 will play $T$ w.p. $p$ and $B$ w.p $1-p$. Player 2 will play $L$ w.p $q$ and $R$ w.p $1-q$. Therefore this game will always have a NE. 


## Problem 3
The following are the utility functions of the Labour and Conservative parties. 
$$u_L(x,y) = \frac{x}{x+y}-x, \quad u_c(x,y)=\frac{y}{x+y}-y$$
1. Show that Labour's best-reply function is given by $B_L(y)=\sqrt y - y$. What is the Conservative party's best-reply function?

We want to maximize the share of votes $x$ as a function of $y$, so we take the partial derivative with respect to $x$ and set it equal to zero.

$$\frac {\partial u_L}{\partial x} = \frac{1(x+y)-x(1)}{(x+y)^2} - 1=\frac{y}{(x+y)^2}-1$$
$$\frac{y}{(x+y)^2} -1 = 0$$
$$y=(x+y)^2$$
$$x=\sqrt y - y$$
The second derivative of this 

Therefore Labour's best response function $B_L(y) =  \sqrt y - y$. 

We can do the same for the Conservative parties best response function. This time I will differentiate with respect to $y$ and solve for $y$ as a function of $x$. 

$$\frac{\partial u_C}{\partial y} = \frac{1(x+y)-y(1)}{(x+y)^2}-1=\frac{x}{(x+y)^2}-1$$
$$x=(x+y)^2$$
$$y=\sqrt x-x$$
Therefore conservatives best reply function $B_C(x) = \sqrt x - x$.

2. The Nash equilibrium can be found at the point where $B_C(x^*) = y^*$ and $B_L(y^*)=x^*$. 

$$x = \sqrt y - y$$
$$y = \sqrt x  - x$$
By substitution
$$\sqrt{\sqrt x - x}-(\sqrt x - x) - x = 0$$
$$\sqrt{\sqrt x - x}-\sqrt x = 0$$
Using a graphing calculator I arrive at the solution 
$$x^* = 0.25$$Plugging back into the best-response function for the conservative party. 

$$y^* = \sqrt x  - x = \sqrt {0.25} - 0.25 = 0.25$$

There is also a solution of $y^* = 0, x^* = 0$ but for this part we assume that $x > 0, y > 0$. 

Given the Nash equilibrium of $(x^* = 0.25, y^* = 0.25)$ the vote shares for each party would be 
$$v_L(y^*, x^*) = \frac{0.25}{0.25+0.25}=0.5, v_C (y^*, x^*) = \frac{0.25}{0.25+0.25}=0.5$$
Both parties would receive exactly 50% of the vote. 

3. Plot the best-reply functions, and identify the equilibrium. 

![[Screen Shot 2022-10-20 at 12.19.51 PM.png]]
There are two equilibriums at $(x^* = 0, y^* = 0)$ and $(x^* = 0.25, y^* = 0.25)$. 

4. Assuming $x=0$ and $y = 0$ are possible choices, the vote share payoffs will both be $0/0$ which is undefined. This means that these choices do not make logical sense, and $(0, 0)$ cannot be a valid Nash equilibrium. 
5. No, these payoffs do not make sense as mentioned above. 



https://saylordotorg.github.io/text_introduction-to-economic-analysis/s17-03-mixed-strategies.html

