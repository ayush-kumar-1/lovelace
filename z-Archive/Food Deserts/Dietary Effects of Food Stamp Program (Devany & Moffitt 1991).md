Devaney & Moffitt introduce the model of demand that can be estimated using OLS. The model begins with a utility function for a household.
$$U(Q_1, Q_2, \dots, Q_j, C)$$
Where the household chooses between $Q = 1, \dots, J$ foods and a composite nonfood good $C$. 

Let 
- $Y$, be the total cash income, excluding food stamp benefits
- $B$, be the food stamp benefit  
- $P_j$ the price of food j relative to the price of $C$ 

$$Y + B = \sum_{j=1}^J P_jQ_j+C$$
The income plus the food stamps benefits are spent between the the $J$ food goods. Rearranging the equation we arrive at $J$ different demand functions for food goods. Total income and benfits are entered into the equation seperately. 
$$Q_j = f_j(P_1, P_2, \dots, P_j, Y, B)$$
To include nutrients in this model assume there are $K$ nutrients $N_k, k = 1, \dots K$, and that each unit of food good yields $a_{kj}$ of nutrient $N_k$. The $K$ nutrient equations can be written as follows 

$$N_k=\sum_{j=1}^Ja_{kj}Q_j, k=1,\dots, K$$
These equations together constitute a true model of deteminants of nutrient level. By introducing total income $Y$ and benefits $B$ into the equation seperately we can quanity the income effects for these food goods. For normal goods these effects will be positive and for inferior goods these effects will be negative. 

There is an issue of model specificaiton bias. It is difficult to identify the impact of $B$ specifically on the demand for a particular nutrient. $Y$ and $B$ are too entangled to specfically understand the impact of $B$. The solution is to subsitute the demand equations into the nutrient equations resulting in the following set of reduced form nutrient equations 

$$N_k = g_k(P_1, P_2, \dots, P_j, Y, B)$$
In this reduced-form the nutrient demand is function of prices, food stamp benefit level, cash income, and other variables affecting the demand for food goods. 

$$N_{ki} = \alpha_k + \beta_kY_i+\delta B_i+X_i\phi_k + \varepsilon_{ki}$$
## Data and Empirical Results 

The data comes from (n=2900) households in the Survey of Food Consumption in Low-Income housheolds (SFC-LI). The survey was conducted from November 1979 through March 1980. Data consisted of 
- Food purchased with cash, credit, or food stamps, or other food programs 
- Other variables include particaption in Food Stamps, participation in other food assistance programs (School Lunch, School Breakfest, and WIC), household consumption, income, education, and employment. 
- Data on household food energy and nutrient availability are calculatd from the quantity of each food item used form household food supplies. Total household availabilty of food energy and nutrients is derived by suming the food energy and nutritive value of individual food items used.
	- Proportion of food-at-home vs. food-away-from-home are used, but nutrition qualities for FAFH were not available. 
- Households in the sample contain at least one person having 10 or more meals from household food supplies during the 7 days preceding the interview. 
- Equivalent Nutritional Units (ENU), the number of adult-equivalent males (AME) eating meals from household food supplies adjusted for age-sex composiation. 
- 11 Major Nutrients were evaluated 
	- Calories 
	- Protein 
	- Vitamin A 
	- Vitamin C
	- Thiamin 
	- Riboflavin 
	- Vitamin B6
	- Calcium 
	- Phosphorus 
	- Magnesium 
	- Iron 
- Adjustment variables 
	- FSP Participation 
	- Cash Income 
	- Food Stamp Benefit 
	- Subsidy Value of School Lunches 
	- Subsidy Value of School Breakfasts 
	- Value of home-grown food 
	- Value of gift/pay food
	- AME
	- Female head
	- Guest meal per AME
	- Region (North Central, South, West)
	- Hispanic 
	- Suburban
	- Black
	- Age of Head of Household 

No-way to replicate


