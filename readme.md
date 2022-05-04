# __AppraiseMe: A real estate pricing app__
## Table of Contents

* [Overview](#overview)
* [Business Problem](#Business-Problem)
* [Results and Analysis](#Results-and-Analysis)
* [Future Directions](#Future-Directions)


## Overview
The goal of this project was to develop a predictive model using multiple linear regression for housing sale prices. The data used for this development came from real estate sales records from Kings County, Washington for the years 2014 and 2015. Starting with a baseline model, we improved upon it iteratively all while upholding the assumptions underlying linear regression.

![Price Distribution](price-distribution.png)

## Business Problem
We are developing an app that allows users to enter in basic information about their property and get a reasonably accurate appraisal of the price they might see if they were to sell. The app would use a linear regression model to take in the user-supplied information and return the estimate. 

Our presentation will take the form of an initial elevator pitch promoting the power of our regression model to return reliable and reasonably accurate appraisals.

## Business Questions
1. Which feature is the strongest influence on price?
2. Which features scale and which act like constants?
3. Should a user add an extra bedroom to raise home value?


## Regression Modeling and Results 


__Baseline Model__
* R-squared Score:  0.494
* RMSE:             $257580

__Model 1__
* R-squared Score:  0.672
* RMSE:             $207028

__Model 2__
* R=squared Score:  0.679
* RMSE:             $204791

__Model 3__
* R-squared Score:  0.711
* RMSE:             $194447

__Model 4__
* R-squared Score:  0.759
* RMSE:             $193634


## Analysis
Model_4 was the winner, with an r-squared of 0.76. This means that our model can account for over 3/4 of the variation in the data.

The X and y for this model had been log(X+1) transformed to normalize it, as the data were very heavily right-skewed. We used X+1 to account for the fact that the log of 0 is undefined, and such values would break the model. By adding one, you get rid of the zeroes in the binary and dummy columns.

The coefficients represent the dollar amount per unit change the total price is increased or decreased by. In the case of sqft_living, for each one square foot increase, the value of the home increases by $133.04. For each bedroom, on the other hand, you can expect the overall price to drop by $43257.61!

The binary and dummy features work a little differently. Rather than scaling with unit change, the coefficients are added onto the price if the given property has that feature. For example, if your property falls under grade_13 Mansion, you're looking at a $2,150,458.26 boost to your price!


## Limitations and Future Directions
Even though we included the geographic features in the model, their presence does not entirely make sense. A zipcode coefficient of X is X for all zipcodes, but not all zipcodes are the same. We need to find a way to put these features to better use--perhaps using them as a reference for distance to some attraction?

It might also be worthwhile to test our model against current sales data to see how well it's held up. It may be the case that the model is too tightly fit to the conditions of those two years, and no longer represents the market as it exists now.