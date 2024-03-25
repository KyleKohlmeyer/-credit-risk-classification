# -credit-risk-classification
All work in this repository is my own.

## Overview of the Analysis

The goal of this analysis is to predict whether a loan is healthy or unhealthy based on variables such as loan size, interest rate, debt, ect.
The full list of variables used in the prediction can be found in the included CSV file. 
The loan status is represented by 0 (healthy loan) and 1 (unhealthy loan).

Supervised machine learning was used to create a model to predict the loan status. This means that the model was given training data where it knew the true outcome and was fit to that data, and then was tested on data it had not previously seen and did not know the true outcome.
To accomplish this, the loan data in the CSV file was divided into training and test groups using the SKlearn module. The training data was used to create the model, which was then tested on the test data. The confusion matrix and classification report are for the results from analyzing the test data with the model.

The algorithm used was logistic regression, which is an algorithm that uses a curve to predict binary outcomes given a set of variables (in this case, healthy loan vs unhealthy loan). This algorithm works by fitting logistic curves to the training data and selecting the one that maximizes the likelihood of outcome for all datapoints, and then using this curve to predict what the outcome will be for new datapoints based on where those new points fall on the curve. The confusion matrix and classification report describe how well the testing data fit the model, and these metrics are discussed in the results sections 

## Results

The logistic regression model as a whole had an accuracy of 0.99, which is good on the surface. However, there are many more healthy loans than unhealty loans, so this accuracy metric is deceiving when it comes to predicing the unhealthyness of a given loan. 

Healthy loan (0): 
- precision 1.00  
- recall: 1.00 
- F1: 1.00

The high precision score means that if a loan is predicted to be healthy, it most likely is healthy. The high recall means that most healthy loans are captured as such by the logistic regression algorithm. F1 is a measure of both precision and recall, and since they are both very high, it too is very high. These high scores may not be very useful if the main goal of the algorithm is to find unhealthy loans rather than confirm that a loan is healthy. 

Unhealthy loan (1):
- precision: 0.87 
- recall: 0.89 
- F1: 0.88 

The precision score of 0.87 means that, if a loan is predicted to be unhealthy, it actually is unhealthy 87% of the time. This means that 13% of the time, a loan that is healthy is predicted by the algorithm to be unhealthy. The 0.89 recall score indicates that 89% of unhealthy loans are correctly labeled as unhealthy by this model. As above, the F1 score is a measure of both precision and recall and thus its value falls in the same ballpark.

## Summary

If the goal is to identify the healthy loans from the dataset, them the model is very effective. However, the model was substantually less effective at correctly identifying unhealthy loans, which is not ideal if the goal is to identify which loans are at risk. Given that unhealthy loans can cost banks a lot of money and harm the economy, and given that a given loan is usually assumed to be healthy unless told otherwise, it can be argued that it is much more important to discover which loans are at risk of defaulting. With a precision score of 0.87 and a recall score of 0.89 for predicting unhealthy loans, the model leaves a lot to be desired, given that each unhealthy loan that goes undectected is a large monetary risk for the bank and each healthy loan classified as unhealthy can waste bank resources and cause consequences for the borrower. Thus, I would not recommend using this model, as I would want precision and recall scores for unhealthy loans to ideally be above 0.95 given the stakes for this use-case.  

## Data
The loan data used for the analysis can be found in the resources folder for this repository.