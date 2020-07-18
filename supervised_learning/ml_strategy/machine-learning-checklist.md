# Task Sheet for ML Projects

## Define the Problem from a High Level View

* Nature of the problem
  * Classification
  * Regression
* Type of solution
* Metrics to measure
* Is ML right for this problem
* Manual approach to solve the problem
* Assumptions for the problem

## Identify Data source and Acquire Data

* List sources and the amount of data
* Check if space is an issue
* Check if you are authorized to use the data 
* Acquire the data and convert it into a workable format
* Check the type of data 
* Keep aside a sample of it for testing

## Initial Data Exploration

* Use Jupyter notebook
* Identify the target variable
* Identify the types of features
  * Categorical
  * Numerical
  * Textual
* Analyze the correlation between features
* Add a few data visualizations for easy interpretation of the impact of each feature on the targetvariable
* Documen the findings

## Exploratory Data Analysis

* Write functions to transfor data and automate the process
* Write functions to clean the data
  * Imputing missing values
  * Handling outliers
* Write function to select and engineer features
* Write fucntion to format conversion of features
* Standardize and scale the features

## Develop a baseline model and explore other models to shortlist the best one

* Create a very naive commonly used model which should serve as the baseline for all other complex models
  * SVM
  * Linear Regression
  * Naive Bayes
  * use default parameters
* Measure and compare performance of each model with the baseline model and with each other
* Employ N-Fold cross validation for each model and compute the mean and standard deviation of the performance metrics of the N folds
* Study the features that have the most impact on the target
* Analyze the types of errors the models make while predicting
* Engineer the features in a different manner
* Repeat the above states a few times to be sure that we have ised the right features in the right format
* shortlist the top models based on their performance measure

## Fine tune shortlisted models and check for ensemble methods

* Hyperparameter training using cross validation
* Use automated tuning methds like random search or grid search o find out the best configuration for your best models
* Test ensemble methods like voting classifiers
* Test the mdoels with as much data as possible
* Once finalized use the unseen test sample that was kept aside in the beginning to check for overfitting and underfitting

## Document Code and Communicate your solution

* Document the code as well as your approach and journey throughtout our project
* Create a dashboard like voila or an insightful presentation with close to self explanatory visualizations
* Write a blog/report capturing how you analyzed the features, tested different transformations, etc. Capture your learning\(failures and techniques that worked\)
* Conclude with the mai outcome and future scope\(if any\)

## Deploy your model in production, Monitor!

* Save your final trained model into an h5 or pickle file
* Serve your model using web services
* Connect the input data sources and set up the ETL pipelines
* Manage dependencies using pipenv, or docker, or kubernetes
* You can use AWS, Azure, GoogleCloud platforms to deploy your service
* Monitor the performance on live data or simply for people to use your model with their data

