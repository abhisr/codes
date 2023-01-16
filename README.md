# codes
## COMMENTS

1. Defining churn in strict terms is tricky, as the customer can come back anytime, as evident from data later.
2. **Demographic data about the user is missing**, limiting the Approaches to model the churn.
3. Distribution of Time suggests that it is in UTC and neets to be shifted by 5.5 hours to align with Indian timings.
4. 95% of users have done 33 or less trnsactions. Users can be segmented based on no of transcations, Aggregate value of transactions, and may be, by timing or transacations.
5. Based on transaction frequency of customers:

    > A larger number of users have very low number of transaction over given time period:
    >> 6579 with only 1 |
    >> Around 14000 with less than or equal to 5 (including 1)
    
    Out of total 23k users for given four months.
6. No of transactions is increasing with time (looking ast monthly/weekly data) and accounting for truncations in beginning/end. On Saturday and Sunday, the transactions are little high. For montlhy data, there is little bit dip in number of transaction in mid of the month.

Mean time between consecutive tranactions is calculated for all users. (It does not account around 6000 users). We find the 95th percentile is around 44 days and 99th percentile is around 80 days. 

## CHURN
Tried to Define Churn in terms of a cutoff period when no transaction are being done. However, A Direct cutoff to define the Churn might not be right as the customersmight come back, even after longer times, but the probability will be low as visible in  table couting customers who churned based on a filter of six week and then counting among those who came back.

**Hence we need to fit a Joing distirbution based on 'Age' and time since last
transaction for the customer to undestand churn.**

## Utilizing CLV Models for Churn Prediction
### library lifetimes in python

Fitted BetaGeoFitter on frequency, recency and age of customer assuming that the transactions started from given date.


![image](https://user-images.githubusercontent.com/4462847/212621199-fbd3651a-60d7-43d5-966d-ed25f5293988.png)

## CLV for Top users
 Based on transctions count, top 5% users have around 33 or more transactions per year.
 
 Assumeing 10 years period and 5% margin.
 
**Note:** Use of DCF to get CLV requires assumptions on Growth/Inflation, operating margins, risk factors on company  and risk free rates (for determining the discounts the cash flows), and Expenditure to get the customer (for net margins) and capital needed to be maintained to serve the customer (to get the actual cash flow) and can be played along to fit any number due to lot of variables. 

Hence, estimating CLV with very basic model, for a lifespan to total 10 years and margins of 5 percentage.
