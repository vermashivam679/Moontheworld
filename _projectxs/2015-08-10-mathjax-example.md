---
layout: post
title:  "Forecast Enhancements"
date:   2015-08-10
excerpt: "Incorporated pricing changes in the forecast using price elasticity of demand to enhance inventory allocation."
tag:
- markdown 
- mathjax
- example
- test
- jekyll
feature: https://raw.githubusercontent.com/vermashivam679/Moontheworld/master/assets/img/enhancement.jpg
comments: false
---

### Overview  

- Incorporated pricing data to forecast class-fare of class-level demand forecast to also give demand curve for the flight to depart.  
- The fare adjustment algorithm changed the new forecast to adjust according to the fare structure decided by the market analyst.  
- This enhancement linked pricing strategy and inventory allocation for effective Revenue Management.  
- Improved the runtime of forecasting methodology from \\(8\\)hrs to \\(4\\)hrs (\\(50\%\\) reduction) using double the historical data and with class-fares for fare adjustment.  


### Project Details:  

#### Forecasting Price with demand:  
- Initially, there was no database of class-fares being offered. Using historically saved `R` images of *RMNext* Runs, I extracted the latest captured fares for a historical flight.  
- Setup an automated process for capturing fares from RMNext offered within \\(7\\) days to departure of a flight in the fare database.  
- Using demand curve the algorithm could adjust the forecasted demand using new fares offered in the market and demand curve using fare & demand in the forecast output.  


#### Increasing Efficiency of Forecasting Algorithm:  
- Mentored a new joinee to work on shifting the forecasting process from `SQL` to `R` to reduce manual intervention, use more historical data, increase effciency & dynamicity of the model.  
- Used `data.table` framework in R, vectorised the code and divided the process in \\(2\\) equal batches to run in parallel.  
- This increased the flexibility for a market analyst to choose more and appropriate historical data for forecasting market demand.  

    

$$
\begin{align*}
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{align*}
$$
