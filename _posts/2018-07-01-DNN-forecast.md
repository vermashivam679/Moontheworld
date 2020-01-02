---
layout: post
title:  "Neural Networks based Airline Passenger Load Pickup Forecasting"
excerpt: "Developed route specific Neual Network models for more than 400 routes to predict unconstrained cabin-level load factor pickup for flights to depart 90 days in future."
tag:
- Deep Learning
- DataScience
- Forecasting
feature: https://raw.githubusercontent.com/vermashivam679/Moontheworld/master/assets/img/Neural_nets.jpg
comments: false
---

### Overview
- This forecasting project tries to build a model to predict the number of passengers that will book a travel ticket in the remaining days to departure of a flight.  
- The models were trained on the last 3 years worth of travel for a booking window of 90 days to departure.
- Every route has a separate model based on its history (New routes take the history of a similar route as proxy).
- The forecast period is for future 90 departure dates for a network of around 1400 daily flights.
- Captured the impact of capacity changes, competition flight positioning, seasonality, current booked position, Net Days Out (NDO), holidays & breaks on demand forecasting.
- The models took 8 times the current runtime to train & predict, had higher complexity, lesser interpretability & worked better than simple additive pickup model only on 70% of the network.  


### Details of the Research:

This research was aimed at improving cabin level Passenger Load Pickup Forecasting with Deep-Neural Networks against the conventional Additive Pickup model. The application of machine learning techniques in the airline industry still remains a challenge mainly because of the unavailability of high-quality data and high dependence on simple & interpretable models.  

#### Model Selection
The first step of the study was to compare the performance and feasibility of various machine learning techniques. Neural Networks (by $$H_{2}O.ai$$) showed promising results with lesser runtime, space usage, and better scalability. The below figure shows the comparison of various models that were tried.  

<figure>
	<a href="https://raw.githubusercontent.com/vermashivam679/Moontheworld/master/assets/img/RMSE_comparison_models.jpg"><img src="https://raw.githubusercontent.com/vermashivam679/Moontheworld/master/assets/img/RMSE_comparison_models.jpg"></a>
</figure>

> *Fig. 1- RMSE comparison of Additive Pickup Model (ADP), Linear Regression (Reg.), Neural Networks (NN), Support Vector Machines (SVM) & XGBoost (XGB) on sample data of a high traffic route by Net Days Out (NDO)*  


For the above comparison of models, common set of variables were used in model building. Since Load pickup of a flight is predominantly driven by current booked position & Net Days Out (NDO), feature selection was not done on these features. Standard feature selection methodology was used:  

- **Cleaning Variables:** Removing variables which are constant throughout the data, outlier treatment & missing value imputation.  
- **Standardization & Transformation:** Standardizing numeric variables (standardization is done to remove false collinearity between 2 variables).  
- **Multicollinearity:** Iteratively removing collinear variables with $$VIF>10$$.  
- **Correlation:** Removing variables with Pearson’s correlation coefficient> $$0.5$$. If two variables have a high correlation, the program function looks at the mean absolute correlation of each variable and removes the variable with the largest mean absolute correlation. Correlation is re-evaluated after each step.  
- **Correlation Check:** Logically correlated variables are forcefully removed and only the most important one is kept.  
- **Un-standardization:** variables after feature selection are transformed back to their original scale and original mean.  

<figure>
	<a href="https://raw.githubusercontent.com/vermashivam679/Moontheworld/master/assets/img/Sample_model_performance.jpg"><img src="https://raw.githubusercontent.com/vermashivam679/Moontheworld/master/assets/img/Sample_model_performance.jpg"></a>
</figure>

> *Fig. 2- Performance of Neural Networks (NN) & Additive Pickup (ADP) Models on sample data of a high-traffic route by Departure Date of a Flight*  



#### Neural Network Architecture & Hyper-Parameter Tuning for Each Route:
Models for each route were trained on R with $$H_{2}O.ai$$ platform with controlled CPU & memory usage. Deep Neural Networks were trained based on the following parameters:
- **Data Weightage:** Recent data is given more weight because of changing market parameters that are difficult to capture.  
- **K-fold Cross-Validation:** K is taken between $$5$$ to $$10$$ based on the amount of training data using the formula: `minimum(10, maximum(5, round(rows in training data/10,000)))`.  
- **Network Architecture:** Number of weights in the network is calculated based on the amount of data available for training, such that there is $$1$$ weight per $$1000$$ rows of data. The final architecture is decided by simulating results based on different architectures in a 2 hidden layer network and the constraints on the overall number of weights in the network.  
- **Activation Function:** By testing on sample routes rectifier worked as the best activation function and if the model fails to train, for example- on new routes, then Tanh was used.  
- **L2 Regularization:** range of lambda (regularization rate) was tuned based on the lowest RMSE value. Models were trained at `lambda=0.040` and the resultant weights of the network are used as a starting point for subsequent iteration by taking `lambda=0.025`.
- **Early Stopping & Convergence Threshold:** maximum number of $$10,000$$ iterations are given for proper convergence of the models, such that moving average of the latest $$10$$ iterations of RMSE does not improve by $$0.1\%$$.  
- **Diagnostic Checks:** if adjusted R2 of the model is less than $$0.6$$ or RMSE is more than $$15\%$$ then these models were discarded. If the average directional impact of covariates on the dependent variable is not justified then also these models were discarded.  






