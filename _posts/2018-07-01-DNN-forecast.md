---
layout: post
title:  "Neural Networks based Airline Passenger Load Pickup Forecasting"
excerpt: "Developed route specific Neual Network models for more than 400 routes to predict unconstrained cabin-level load factor pickup for flights to depart 90 days in future."
tag:
- Deep Learning
- Neural Networks
- Demand Forecast
- Machine Learning
- R
- SQL
- H2O.ai

feature: https://raw.githubusercontent.com/vermashivam679/sv1992/master/assets/img/Neural_nets.jpg
comments: false
---

### Overview
- This forecasting project tries to build a model to predict the number of passengers that will book a travel ticket in the remaining days to departure of a flight.  
- The models were trained on the last 3 years worth of travel for a booking window of 90 days to departure.
- Every route has a separate model based on its history (New routes take the history of a similar route as proxy).
- The forecast period is for future 90 departure dates for a network of around 1400 daily flights.
- Captured the impact of capacity changes, competition flight positioning, seasonality, current booked position, Net Days Out (NDO), holidays & breaks on demand forecasting.
- The models took 8 times the current runtime to train & predict, had higher complexity, lesser interpretability & worked better than simple additive pickup model only on 70% of the network.  








