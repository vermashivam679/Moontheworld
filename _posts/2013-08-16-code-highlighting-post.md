---
layout: post
title: Long Term Route level Forecast using Linear Regression
date: 2013-08-16
excerpt: "Developed route specific travelled Load Factor forecasting models for future 365 days of departure."
tags: [sample post, code, highlighting]
comments: false
---


### Overview  
Using this project I tried to solve for following problems:  
- We needed a more scientific financial reporting system to show accurate load factor forecasts for *Annual Operations Planning (AOP)*.  
- Forecasting was done only for //(120//) days of departure outside which inventory was managed with a more aggressive strategy leading to lesser bookings.  
- Forecasting method didn't include impact of holidays & festivals which was only captured in the current booked position.  

### Details  
- Indian festivals are not equally popular in every region. But public holidays, summer & winter have a similar travel pattern across the country.  
- Analyzing the holidays we created a pool of important holidays & breaks to segment them into broad categories including Religious holidays, weekend holidays, Special festivals like Diwali/Holi etc.  
- Identified the behaviour of holidays with respect to Day of Week & Month of Year and coded that into the variables.  
- Assessed the performance of various models like ARIMAX, exponential smoothing methods and Bayesian structural time series modelling to finalize linear regression, because of its intelligibility and competent accuracy.  








