---
layout: post
title:  "Fleet Management of Buses using Survival Analysis & Genetic Algorithm"
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
- We developed Survival Analysis models for each component to predict their probability of failure in the next N(business variable) weeks and optimized preventive & reactive treatment costs


### Project Details:  
- Stratified the data by fleet between train, validation & test datasets and evaluated the performance of models based on AUC-ROC curves on test & validation data  
- Used Cox-proportional hazard modeling for predicting the probability of failure in next N weeks for 8 main vehicle components
- Optimized time-varying probability cut-offs by minimizing net maintenance cost (~10% reduction) using Genetic Algorithm






