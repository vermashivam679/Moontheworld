---
layout: post
title: "Fare Restructuring & Forecast Fare Adjustment Algorithm"
excerpt: "Restructured the fares to remove fare values that didn't sell and match fare values closer to competition. The impact of changing the Fare-structure on the forecast was captured by the fare adjustment algorithm."
tags: [sample post, images, test]
comments: false
---


### Fare Restructuring  [<kbd>6E Achiever(Employee of the Month)</kbd>](https://raw.githubusercontent.com/vermashivam679/Moontheworld/master/assets/img/Fare_restructuring_6e_achiever.jpg)
- Using Historical data estimated market level demand curve using Monotone Spline Interpolation.
- Maximized revenue by optimizing fares on demand curve using shortest path algorithm. The fare values considered for optimization were market competition's fares scrapped from the web.
- The optimal fares were given as a suggestion to the market operations team.
- Estimated impact of fare restructuring on revenue to be 1-2% and quick reaction to competition’s fare action.


### Forecast Fare Adjustmet  
- Due to fare restructuring the fares of fare-buckets changed drastically, therefore class-level forecast was not in-line with the fares.
- To capture this impact we created a demand curve of the forecasted demand and using route-level constant historical fare structure.
- Using the demand curve we could forecast demand for new fare structures given by the market analyst.




