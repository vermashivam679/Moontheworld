---
layout: post
title:  "Fleet Management of Buses using Survival Analysis and Genetic Algorithm"
date:   Sep’17 –Dec’17
excerpt: "This was a Predictive Vehicle Maintenance project for a UK based Bus Transportation Company"
tag:
- Operations Research 
- Large-Scale Project
- Data Science
- Airlines
- jekyll
feature: https://raw.githubusercontent.com/vermashivam679/Moontheworld/master/assets/img/Predictive-Maintenance-Strategies.png
comments: false
---

### Overview  
- A UK based public transportation company was interested in predicting the failure of its 8 vehicle components.
- We developed Survival Analysis models for each component to predict their probability of failure in the next 4 weeks and optimized preventive & reactive treatment costs


### Project Details:  
- I stratified the data by fleet between train, validation & test datasets and evaluated the performance of models based on ROC curves & AUC on test & validation data  
- Used Cox-proportional hazard modeling for predicting probability of failure in next N(upto 8) weeks for 8 main vehicle components
- Optimized time varying probability cut-offs by minimizing net maintenance cost (~10%) using Genetic Algorithm






