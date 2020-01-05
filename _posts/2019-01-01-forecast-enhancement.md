---
layout: post
title:  "Forecast Enhancements"
excerpt: "Incorporated pricing changes in the forecast using price elasticity of demand to enhance inventory allocation."
tag:
- Econometrics
- Demand Forecast
- Inventory Optimization
- Revenue Management
- R
- SQL
feature: https://raw.githubusercontent.com/vermashivam679/Moontheworld/master/assets/img/enhancement.jpg
comments: false
---

### Overview  

- Incorporated pricing data to forecast class-fare of class-level demand forecast to also give demand curve for the flight to depart.  
- The [fare adjustment algorithm](https://vermashivam679.github.io/Moontheworld/fare-realignment/) changed the new forecast to adjust according to the fare structure decided by the market analyst.  
- This enhancement linked pricing strategy and inventory allocation for effective Revenue Management.  
- Improved the runtime of forecasting methodology from \\(8\\)hrs to \\(4\\)hrs (\\(50\%\\) reduction) using double the historical data and with class-fares for fare adjustment.  





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
