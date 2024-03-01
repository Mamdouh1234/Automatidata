# Automatidata-New-York-City-TLC
A Machine Learning model for classifying New York City Taxi and Limousine Commission customers to either generous or not according to their tip.


## Overview 

The goal of this project was to create a predictive model that predicts customer type as generous or not ,  for New-York-City-TLC
We trained three models which are  NaiveBayes , RandomForest and XGBOOST.
The champion model was Random Forest with F1-score 0.752.

## Business Understanding 

Automatidata works with its clients to transform their unused and stored data into useful solutions, such as performance dashboards, customer-facing tools, strategic business insights, and more. They specialize in identifying a client’s business needs and utilizing their data to meet those business needs. 

Automatidata is consulting for the New York City Taxi and Limousine Commission (TLC). New York City TLC is an agency responsible for licensing and regulating New York City's taxi cabs and for-hire vehicles. 
**The agency has partnered with Automatidata to develop a classification model that helps classify customers as generous or not according to their tips.**

A machine learning model would greatly assist in the effort to present human moderators with videos that are most likely to be in violation of TikTok's terms of service.

## Data Understanding

The data consisted of approximately 22699 rows and 21 features. The features included information on customers trips such as: 
- VendorID               
- tpep_pickup_datetime   
- tpep_dropoff_datetime 
- passenger_count        
- trip_distance          
- RatecodeID             
- PULocationID           
- DOLocationID           
- payment_type           
- fare_amount            
and more

**Note**: the target variable "generous" didn't exist in the original dataset , it was engineered later in the Analyze stage.

## Modeling and Evaluation 

We trained three models which are:
 - NaiveBayes
 - RandomForest
 - XGBOOST

Cross Validation technique was applied , the dataset was splitted to 70% for training , 15% for validation and 15% for unseen testing data which will be used to evaluate our champion model.
   
considering accuracy measures , for each model , we output a confusion matrix and four accuracy measures , they are
 - Accuracy
 - Precision
 - Recall
 - F1 Score
   
In the given scenario, False positives are worse for cab drivers, because they would pick up a customer expecting a good tip and then not receive one, frustrating the driver.

False negatives are worse for customers, because a cab driver would likely pick up a different customer who was predicted to tip more even when the original customer would have tipped generously.

**We want to help taxi drivers make more money, but we don't want this to anger customers. our metric should weigh both precision and recall equally. this metric is F1-score.

The champion model was **RandomForest** with F1-score 0.752 on the validation set.

The model Scored 0.743 on the unseen testing set.

## Conclusion

- The model performed quite well on validation and test sets , however, it could be improved by doing more feature engineering , In our case, we could try creating three new columns that indicate if the trip distance is short, medium, or far. We could also engineer a column that gives a ratio that represents (the amount of money from the fare amount to the nearest higher multiple of $5) / fare amount. For example, if the fare were $12, the value in this column would be 0.25, because $12 to the nearest higher multiple of $5 ($15) is $3, and $3 divided by $12 is 0.25. The intuition for this feature is that people might be likely to simply round up their tip, so journeys with fares with values just under a multiple of \\$5 may have lower tip percentages than those with fare values just over a multiple of $5. We could also do the same thing for fares to the nearest $10. the ratio we are talking about is shown below:

$$
round5\_ratio = \frac{amount\ of\ money\ from\ the\ fare\ amount\ to\ the\ nearest\ higher\ multiple\ of\ \$5}{fare\ amount}
$$

- It would probably be very helpful to have past tipping behavior for each customer. It would also be valuable to have accurate tip values for customers who pay with cash.
It would be helpful to have a lot more data. With enough data, we could create a unique feature for each pickup/dropoff combination.
