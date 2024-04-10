<img src="readme_photos/ai_cover_photo_bike.jpg" style>
<h1 align="center">Cycles of Demand: Predicting Washington DC's E-Bike Rentals Usage </h1>


<a href="https://nbviewer.org/github/BrianMillerS/ebike_usage_regression/blob/main/ebike_regression_analysis.ipynb" target="_blank">Jupyter Notebook Viewer</a>  <br><br>
<a href="https://raw.githubusercontent.com/BrianMillerS/ebike_usage_regression/4b5c92868da7195f29ce5d69f1c4bfb0d9f21a0b/BM_ebike_usage_presentation.pdf" target="_blank"> Download Powerpoint Presentation</a>
<br>

# Table of contents
- [Project Takeaway](#Project-Takeaway)
- [Description of the Data](#Description-of-the-Data)
- [Methods Overview](#methods-overview)
- [Project Summary](#project-summary)

# Project Takeaway
The goal of this project was to understand the patterns of E-bike usage and create a predictive model that can forecast the number of riders per hour based on time and weather conditions.
- Six models were tested: Linear Regression, Decision Tree Regressor, Random Forest Regressor, SGD Regressor, Bagging Regressor.
- Random Forest Regressor had the best performace after parameter tuning with a R^2 = 0.89 and RMSE = 0.33 (6-fold xval).
- Warmer weather, less humidity, and it being rush hour times were the best predictors of E-bike usage.

The insights from this project could enable Capital Bikeshare and similar companies to make evidence-based decisions about where and when to allocate resources, leading to increased operational efficiency and customer satisfaction. 
<br> Potential business changes could include:
 - Increase E-Bike redistribution before rush hour to capitalize on commuter usage.
 - Add E-Bike charging stations near dense employment locations.
 - Offer discounts or incentives during no-optimal weather conditions.
 - If E-Bike rollbacks or updates need to be done, perform them during non-peak
months

# Description of the Data
The data was downloaded from <a href="https://archive.ics.uci.edu/dataset/186/wine+quality" target="_blank">UC Irvine’s curated repository</a> of datasets for machine learning. The data consisted of a single table with 1600 rows, each containing data on a specific portuguese red wine variant. Along with the wine’s quality score (the median score from three professional wine tasters) the table also had eleven other columns with measured physicochemical properties.

# Methods Overview
+ Exploratory Data Analysis
  + Checking Data Quality
  + Visualizing Numeric and Categorical Predictor Variables
+ Model Building
  + 
  + 
  + Bagging Regressor 
  + Random Forest Regressor
+ Model Parameter Tuning
  + Grid Search
  + Iterative Randomized Search
+ Model Evaluation
  + Accuracy
  + F1 Score
  + ROC Curve/ Confusion Matrix
  + Identifying the Most Important Variables for Wine Quality Prediction

# Project Summary
- [Exploratory Data Analysis](#Exploratory-Data-Analysis)
- [Model Building](#Model-Building)
- [Model Parameter Tuning](#Model-Parameter-Tuning)
- [Model Evaluation](#Model-Evaluation)
- [Determining Important Variables](#Determining-Important-Variables)

<br>  

## Exploratory Data Analysis  

First lets take a look at all of the data in our dataset.  
We have:  
  - 11 predictor variables  
  - 1 outcome variable (quality)

<img src="images/variable_distributions.png" style>  
<br>

In order to make this classification problem a little easier we will be binning wines into 'good' and 'bad' as follows:
<br>
<img src="images/data_binning.png" style>
<br>

## Model Building  

  - In order to train our models, the data was split into 80% training/ 20% testing
  - Using the default models from Tensorflow here were the results:
<br>
<img src="images/results_summary_table.png" width="532" height="225">
<br>
From this point on in the analysis, we will focus on the two top performing models: Random Forests, and XGBoost

## Model Parameter Tuning
RF and XGBoost performed the best, let's take both models, tune them, and see if we can improve them further.
<br>
A GridSearch was performed on the RF model, this approach is more time and resource intensive, but it is exhaustive, so we will know that we will be getting the best result. 
<br>
<img src="images/RF_results.png" width="498" height="200">
<br>

#### XGBoost Results
A Randomized search was performed on the XGBoost mode, this approach is faster, not exhaustive, but it is quick. To help ensure that we were getting still good results I did the Randomized search 10 times and picked the best result.
<br>
<img src="images/XGB_results.png" width="495" height="298">
<br>

## Model Evaluation
Now with the best model selected, and parameters tuned, we can evaluate the model and see how it performed.
<br>
<img src="images/XGB_confusion.png" style>
 - True Positives (TP): 144
 - True Positives (TP): 144
 - False Positives (FP): 25
 - False Negatives (FN): 27
<br>

The model has an AUC of 0.91, which suggests it has a high accuracy in distinguishing between the classes
<br>
<img src="images/XBG_roc.png" width="532" height="382">
<br>
Overall, the model appears to be performing well, with good predictive power and a balance of error types that lean towards correct predictions.

## Determining Important Variables
<br>
<img src="images/XGB_correlation.png" style>
Both Alcohol and Sulphates are positively correlated with wine score.
<br>

<br>
<img src="images/XGB_gain.png" style>
The scatter plots and feature importance graph together suggest that while many factors contribute to wine quality, alcohol content is potentially the most predictive, followed by sulphates.  
<br>
  
- The least important features suggest that within this dataset and model, aspects like pH and chlorides are not key drivers in predicting wine quality.
- Features related to acidity, such as volatile acidity and fixed acidity, also play a significant role in the model's predictions.
- 

<img src="readme_photos/by_hour_dsitributions.png" style="width: 843px; height: 834px;">

<img src="readme_photos/categorical_distributions.png" style>

<img src="readme_photos/coor_map.png" style="width: 621px; height: 673px;">

<img src="readme_photos/data_example.png" style>

<img src="readme_photos/feature_importance.png" style="width: 882px; height: 675px;">

<img src="readme_photos/multi_model_perf.png" style>

<img src="readme_photos/numerical_distributions.png" style>

<img src="readme_photos/param_tuning_code.png" style>

<img src="readme_photos/predicted_vs_actual.png" style>

<img src="readme_photos/residuals.png" style>
yaa
<img src="readme_photos/seasonality_chart.png" style="width: 723px; height: 541px;">

<img src="readme_photos/temp_hum_lin_graph.png" style>

<img src="readme_photos/test_results.png" style="width: 974px; height: 237px;">



