---
layout: post
title:  "Deep-Neural Networks based Airline Passenger Load Pickup Forecasting"
date:   2016-03-15
excerpt: "Attempt to Implementation: Couldn't go live because of 7(56/8) times higher training time, highly complexity, less interpretability, worked better than simple additive pickup model only on 70% of the network."
tag:
- Deep Learning
- DataScience
- Forecasting
comments: false
---

#### Overview
- This forecasting project tries to build a model to predict number of passengers that will book a travel ticket in the remaining days to departure of a flight. 
- The models trained on last 3 years worth of travel for a booking window of 90 days to departure.
- Every route has a seperate model based on its history (New routes take history of a similar route as proxy).
- The forecast period is for next 90 departure dates for a network of around 1400 daily flights.
- Captured the impact of capacity changes, competition flight positioning, seasonality, current booked position, Net Days Out (NDO), holidays & breaks on demand forecasting.

#### Details of the Research:

This research was aimed at improving cabin level Passenger Load Pickup Forecasting with Deep-Neural Networks against the conventional Additive Pickup model. The application of machine learning techniques in the airline industry still remains a challenge mainly because of the unavailability of high-quality data and high dependence on simple & interpretable models.  

##### Model Selection
The first step of the study was to compare the performance and feasibility of various machine learning techniques. Neural Networks showed promising results with lesser runtime, space usage, and better scalability. The below figure shows the comparison of various models that were tried:  

<figure>
	<a href="http://farm9.staticflickr.com/8426/7758832526_cc8f681e48_b.jpg"><img src="http://farm9.staticflickr.com/8426/7758832526_cc8f681e48_c.jpg"></a>
	<figcaption><a href="http://www.flickr.com/photos/80901381@N04/7758832526/" title="Morning Fog Emerging From Trees by A Guy Taking Pictures, on Flickr">Morning Fog Emerging From Trees by A Guy Taking Pictures, on Flickr</a>.</figcaption>
</figure>

> *Fig. 1- RMSE comparison of Additive Pickup Model (ADP), Linear Regression (Reg.), Neural Networks (NN), Support Vector Machines (SVM) & XGBoost (XGB) on sample data of a high traffic route by Net Days Out (NDO)*

For the above comparison of models common set of variables were used in model buidling. Since Load pickup of a flight is predominantly driven by current booked position & Net Days Out (NDO), feature selection was not done on these features. Standard feature selection methodology was used:  

- Cleaning Variables: Removing variables which are constant throughout the data, outlier treatment & missing value imputation.  
- Standardization & Transformation: Standardizing numeric variables (standardization is done to remove false collinearity between 2 variables).  
- Multicollinearity: Iteratively removing collinear variables with VIF>10.  
- Correlation: Removing variables with Pearson’s correlation coefficient> 0.5. If two variables have a high correlation, the program function looks at the mean absolute correlation of each variable and removes the variable with the largest mean absolute correlation. Correlation is re-evaluated after each step.  
- Correlation Check: Logically correlated variables are forcefully removed and only the most important one is kept.  
- Un-standardization: variables after feature selection are transformed back to their original scale and original mean.  

<figure>
	<a href="http://farm9.staticflickr.com/8426/7758832526_cc8f681e48_b.jpg"><img src="http://farm9.staticflickr.com/8426/7758832526_cc8f681e48_c.jpg"></a>
	<figcaption><a href="http://www.flickr.com/photos/80901381@N04/7758832526/" title="Morning Fog Emerging From Trees by A Guy Taking Pictures, on Flickr">Morning Fog Emerging From Trees by A Guy Taking Pictures, on Flickr</a>.</figcaption>
</figure>

> *Fig. 2- Performance of Neural Networks (NN) & Additive Pickup (ADP) Models on sample data of a high-traffic route by Departure Date of a Flight*






##### Neural Network Architecture & Hyper-Parameter Tuning for Each Route:
Models for each route were trained on R with H2O.ai platform with controlled CPU & memory usage. Deep Neural Networks were trained based on the following parameters:
- Data Weightage: Recent data is given more weight because of changing market parameters that are difficult to capture.  
- K-fold Cross-Validation: K is taken between 5-10 based on the amount of training data using the formula: minimum(10, maximum(5, round(rows in training data/10,000))).  
- Network Architecture: Number of weights in the network is calculated based on the amount of data available for training, such that there is 1 weight per 1000 rows of data. The final architecture is decided by simulating results based on different architectures in a 2 hidden layer network and the constraints on the overall number of weights in the network.  
- Activation Function: By testing on sample routes rectifier worked as the best activation function and if the model fails to train, for example- on new routes, then Tanh was used.  
- L2 Regularization: range of lambda (regularization rate) was tuned based on the lowest RMSE value. Models were trained at lambda=0.040 and the resultant weights of the network are used as a starting point for subsequent iteration by taking lambda=0.025.
- Early Stopping & Convergence Threshold: maximum number of 10,000 iterations are given for proper convergence of the models, such that moving average of latest 10 iterations of RMSE does not improve by 0.1%.  
- Diagnostic Checks: if adjusted R2 of the model is less than 0.5 or RMSE is more than 15% then these models were discarded. If the average directional impact of covariates on the dependent variable is not justified then also these models werediscarded.






Research Experience (Forecasting using Deep-Neural Networks (DNN), IndiGo Airlines, Jun’18 – Present):  
- My current efforts to improve the passenger load forecasting methodology at IndiGo require significant literature review and brainstorming on evaluating & devising the right implementation framework that is also easy to integrate with current processes. At first, I had to solve for only one question which was to improve the forecast but this question opened many others which nobody could accurately answer. I began comparing different well-known models with the existing model to find the best one in terms of run-time, scalability and predictive power. After finalizing deep learning using H2O.ai package on R, I delved further and acquired a deeper understanding focused on topics such as the optimizing ways to tune hyper-parameters, studying the impact of changing those parameters on the performance of the models, incorporating a diagnostic health check on the models and combining with the additive model in place. Lastly, presentation of my work in a structured manner with insightful visualization to other members of the team who don’t have a detailed understanding of the complexity involved in deep learning techniques, has also been an important part of my learning curve that I find of significant value.  




365 Days Forecasting:
> As I explored further into the field of data science, I was fascinated to learn the perpetually growing role of data science in the Airlines industry, targeted to uncover the nuances of its complex operations. This fascination led me to pursue a niche role in the Airlines industry, with Revenue Planning & Analysis team of one of the leading Indian Airlines company – Indigo Airlines, which provided me with a greater platform to implement my knowledge in data science and to delve further. I joined this team in its very initial stage with only 3 members, which meant I had a greater role in the team with more accountability and hence, I could unleash opportunities for rapid growth. While delivering as part of this team, I developed origin-destination level Load Factor Forecasting models for flights departing in future 365 days with automated feature selection. I assessed the performance of various models like ARIMAX, exponential smoothing methods and Bayesian structural time series modelling to finalize linear regression, because of its intelligibility and competent accuracy. Insights from the data helped me find an accurate and unprecedented way of capturing the impact of holidays & breaks on O-D level load factor.





<iframe width="560" height="315" src="//www.youtube.com/embed/SU3kYxJmWuQ" frameborder="0"> </iframe>

Video embeds are responsive and scale with the width of the main content block with the help of [FitVids](http://fitvidsjs.com/).

Not sure if this only effects Kramdown or if it's an issue with Markdown in general. But adding YouTube video embeds causes errors when building your Jekyll site. To fix add a space between the `<iframe>` tags and remove `allowfullscreen`. Example below:

{% highlight html %}
<iframe width="560" height="315" src="//www.youtube.com/embed/SU3kYxJmWuQ" frameborder="0"> </iframe>
{% endhighlight %}
