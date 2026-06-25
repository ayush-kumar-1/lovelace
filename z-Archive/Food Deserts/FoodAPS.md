The National Household Food Acquisition and Purchase Survey (FoodAPS)[^1] is an incredibly detailed survey. The following is an overview of the public use data files. 

The following files are present in the public use downloads.
- faps_fafnutrient_puf.csv
- faps_meals_puf.csv
- faps_fafhitem_puf.csv
- faps_fafevent_puf.csv
- faps_household_puf.csv
- faps_fahnutrients.csv
- faps_individual_puf.csv
- faps_individaul_fahevent_puf.csv
- faps_hhweights.csv
- faps_access_puf.csv

## Household Level

For the variable by variable level see the household data codebook[^3].

[^3]:https://www.ers.usda.gov/media/9139/1_household-codebook-puf.pdf

4,826 households participated in the study, and they were each individually identified by a unique `hhnum` variable. There are four measures of size for each household, `REUNITSIZE`, `HHSIZE`, `FAMSIZE`, `NUMGUESTS`. HHSIZE is the number in the household, which is then broken down into family and guests. `RESUNITSIZE` refers to the number of individuals physically in the unit during the purchase. 

Total household inocme is expressed through `INCHHREPORTED_R`, the total income of the household, and `INCFAMREPORTED_R` which is the family income. These are household-level sums of 6 income categories (earnings, unemployment insurance, retirement, welfare, child support, and alimony). When income was not reported five imputed values were used. `INCHAVG_FLAG` show s when imputations were sued for the categories. 

Four monthly poverly lines are present, 2012 poverty guideline for household `POVGUIDE_HH` and family `POVGUIDE_FAM`. and the 2012 povery threshold for the household and the family `POVTHRESH_HH, POVTHRESH_FAM`. Poverty guidelines only adjust for the household/family size, thresholds adjust for family size and composoition as well. 

SNAP particpation was self-reported and cross-verified to ensure validity. `SNAPNOWADMIN` summarizes the matching process. The dataset also detailed when SNAP benefits were last recieved. 

Monthly household expenditures 
- Rent or mortagage
- Rental or homeowners insurance 
- Property taxes 
- Public Transport 
- Electricity 
- Heating fuel 
- Sewer and garbage/trash removal
- Health insurance
- Health insurance copays 
- Doctor and hospital bills 
- Prescription drugs 
- Child care
- Child support 
- Adult care

These variables are weighted to reflect total monthly expenditures, and if the reported dollar amount is "Don't know" or "Refused" then the recoded variables has the same missing vale code. 

Where households shopped is detailed in the primary store and alternate store variables. These include SNAP information. Using PRIMSTOREPLACEID and ALTSTOREPLACEID these variables can be linked with the event files. 

Food security status, `ADLTFSCAT` is assigned on a scale of 1-4 with 1 being high food security among adults, and 4 being very low food security among adults. SNAP eligiblity is also calculated.

Households with elderly or diasbled persons were also identified. 

Monthly Expenditures on Non-food items 
- These variables include values that are implausibly high or low, suggesting that either the underlying amount or frequency variable was recorded in error. The ERS has made no efoorts to identify or correct reported amounts. Outlier detection may be needed, I reccomend the shapiro-wilk test for outlier detection[^2]

Store distances, walking, and driving times are also listed 
- May be important to understanding time costs 

## Individual Data

`faps_individual_puf` contains one record for each of the 14,317 individuals in the 4,826 households that participated in the data collection. Each individual has a unique `PNUM` and belongs to a houshold of `HHNUM`, so the two variables together uniquely identify an individual. 



[^1]:https://www.ers.usda.gov/data-products/foodaps-national-household-food-acquisition-and-purchase-survey/documentation/ 
[^2]:https://en.wikipedia.org/wiki/Shapiro%E2%80%93Wilk_test