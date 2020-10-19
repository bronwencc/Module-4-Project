
# Module 4 -  Final Project


## Introduction

This is Bronwen C.'s submission for Module 4's Final Project, using house price data from Zillow, provided by Learn.co and The Flatiron School to model, predict and then choose **the top five** zipcodes in which to invest.

## Project
This repository contains:
* Data from Zillow provided by the course in zillow_data.csv
* A [Jupyter Notebook](https://github.com/bronwencc/Module-4-Project/blob/master/mod_4_final.ipynb) with code analyzing and modeling the data from zillow_data.csv
* A PDF of PowerPoint presentation slides explaining the data to a prospective business audience
* Some CSV files of reshaped, reformatted and forecasted Zillow data from various stages in the project
* Three PNG images files of graphs made in the notebook and used in the PowerPoint
* A [LICENSE file](https://github.com/bronwencc/Module-4-Project/blob/master/LICENSE), detailing how or whether this project's code may be repurposed

### Notebook Summary

The notebook reformats the data into DataFrames and then uses SARIMAX in statsmodels to make predictions a few times.  The first time is to find which order and seasonal order parameters best describe the averaged timeseries of all the prices, going by the lowest AIC.  The second time is to find the mean-squared errors for five steps past a training set for the median ninth of the data (44th to 55th percentiles).  The third time is to generate predictions and 95% confidence intervals for the selected 20 RegionID's that had the smallest mean-squared errors for the two-year period following the last observed values.  Of these 20 RegionID's, the five with the highest percent change between the last observed value and the lower bound of the confidence interval of the last predicted value (the highest was -16%) were decided to be the best investments.

### Figures

The PNG images are to compare the 24-step (two years) forecasted values for the data as an average timeseries (Average Forecast.png) and to see the confidence intervals of the 20 RegionID's with the smallest mean-squared error over the same period (20 RegionID Forecasts.png).  The TopFiveDataandForecasts.png is to look at the forecasts in the context of the historical data for the top five selected regions.

### Files

* [zillow_data.csv](https://github.com/bronwencc/Module-4-Project/blob/master/zillow_data.csv) is the original dataset provided by Learn.co and The Flatiron School analyze instead of pulling my own selection from the Zillow website.  It is organized with each region as its own row (for a total of 14,723 records) and columns consisting of descriptive properties (RegionID, City, State, etc.) as well as monthly intervals from 1996-04 to 2018-04.
* [ConfidenceIntervals.csv](https://github.com/bronwencc/Module-4-Project/blob/master/files/ConfidenceIntervals.csv) is the forecasts of 24 steps ahead for each of the selected 20 RegionID's and their 95% confidence intervals.  There are three columns for each RegionID: upper, lower and forecast.
* [MSE-9th.csv](https://github.com/bronwencc/Module-4-Project/blob/master/files/MSE-9th.csv) is the mean-squared errors for the median ninth of the data calculated by forecasting the first five steps of the test set using the training set.
* [pred20.csv](https://github.com/bronwencc/Module-4-Project/blob/master/files/pred20.csv) contains two rows, one for the latest observed value of the 20 RegionID's and one for the lower bound of that RegionID's 24-step forecast's latest value (the worst case scenario for 2020-04).
* [transposedPrices.csv](https://github.com/bronwencc/Module-4-Project/blob/master/files/transposedPrices.csv) is the zillow_data transposed into a format where each column is a RegionID and the index is the series of dates by month.  The other difference is that it does not include those RegionID's that had missing values for any dates.
