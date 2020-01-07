---
layout: post
title: "Fare Restructuring & Forecast Fare Adjustment Algorithm"
excerpt: "Restructured the fares to remove fare values that didn't sell and match fare values closer to the competition. The impact of changing the fare-structure on the forecast was captured by the fare adjustment algorithm."
tags: [Econometrics, Demand Forecast, R, SQL, Competitive Strategy, Revenue Management]
feature: https://raw.githubusercontent.com/vermashivam679/sv1992/master/assets/img/dmd_crv.jpg
comments: false
---


### Fare Restructuring  
- Using Historical data estimated market-level demand curve using Spline Interpolation.  
- Maximized revenue by optimizing fares on demand curve using the shortest path algorithm. The fare values considered for optimization were market competition's fares scrapped from the web.  
- The optimal fares were given as a suggestion to the market operations team.  
- The estimated impact of fare restructuring on revenue was ~2% and the ability to react quickly to competition’s fare action.  


### Forecast Fare Adjustmet  
- Due to fare restructuring, the fare values of price-buckets changed drastically, therefore class-level forecast was not in-line with the fares.  
- To capture this impact we created a demand curve of the forecasted demand and using route-level constant historical fare structure.  
- Using the demand curve we could forecast demand for new fare structures given by the market analyst.  




