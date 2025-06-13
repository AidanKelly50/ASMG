---
title: "Project - Phase IV"
date: 2025-06-13
draft: false
description: "Final Report"
slug: "phase4post"
tags: ["project", "author"]
authors:
  - "aidankelly"
  - "seanbehan"
  - "gabbymontalvo"
  - "mariasamosrivas"
showAuthorsBadges: false
---

# Desciption of ML models

## Traveler Recommender Model
This model asks the user for their input on 3 features, traffic, fuel price, and tourist numbers. It weighs the values on a scale of 0-1 and turns them into a vector. The model then takes the cosine similarity score between the user vector and the vector for each country, where each column is the score for each of the countries. The model then takes the similarity score and returns the top 5 countries that are most similar to the user input on a map. 

It was initially finished as a part of out Phase 3 deliverable

As it is an unsupervised model, there aren’t any assumptions we need to keep an eye out for since no training/testing data was used.


## Tourism Time Series Regression
This other model is a time series model that predicts the tourist trends for the specified country as years go on. This model takes a matrix of shape (26 x 7), as there are 26 countries and 7 features (bias, country, year, covid, lag1, lag2, lag3). All these features accounted for bias, covid years (2020-2021), and the number of years we wanted to predict in the future, 3,  (lag1-lag3). We used the equation: (X.TX)^-1(X.TY) (x-transpose x inverse times x transpose y) to fit the model for one specific country and predict the upcoming years. The r-squared, how reliable this model is, for Slovakia, our country of choice: 77% which shows that the model is reliable. We later plotted our results on a line graph showing the number of tourists in a country over the years. 

After that, we cross validated our results to evaluate how well a model will predict new data. We did this by predicting the already known years and comparing them to the actual value. This r-squared value was 6%, which shows that our model isn’t very accurate at predicting tourist rates. In order to make our model more accurate, instead of just looking at the data from one country, we can look at the data from all EU countries, as it is very likely that they are connected with countries, so our model would have more data it could use to predict it. 

As seen from the residual plot there are some assumptions of linearity that aren’t met. When looking at linearity, the residuals show a very slight pattern of a curve, which is something to keep in mind when looking at the other conditions. The residual graph has a funnel shape, which violates homoscedasticity meaning that there's more spread on the bottom right than top left, thus the distance from the variance isn’t equal across the graph, especially due to the outlier. Finally, there's no autocorrelation, a there doesn't seem like there's a repeated pattern.

In the near future, it would be interesting to see what the plot would look like once the outliers are taken out of the model. The r2 would probably go up, meaning that the predictions would be more accurate.

# Software Architecture and Database Model

#### Architecture

The data is stored in a MySQL database. It is accessed by a Flask REST API. The Front End is in Streamlit, and it accesses the backend through the REST API.

The project is run in a Docker container which holds the MySQL database, API, and web app.

For the pages with graphs and data, the Front End calls the API, which accesses the MySQL database, which sends the data to be used for the Front End. 

For the unsupervised model, the Front End calls the API, which accesses the MySQL database and uses that data to call a backend function that runs the recommender model.

For the supervised model, the Front End calls the API which accesses the already-trained data in the MySQL database to display the results.

For the researcher's posts that can be added, changed, and deleted, the Front End calls the API, which accesses the MySQL database to change the contents of the tables.

#### Final Model

- ![DDL Picture](NewMySQLDDL.png)

Our ER Model has 14 entities. They hold the tourism data, road data, researcher posts, shared graphs, and users. They are all connected via Countries, except for ReasearchFindings and GraphFindings.

This translated to a DDL model with 14 tables.

These tables are accessed using 16 GET routes. The researcher and graph posts can be changed with 2 POST routes, 1 PUT route, and 1 DELETE route:

- ![Tourist Requests](touristRequests.png)
- ![Official Requests](officalRequests.png)
- ![Post Requests](postsRequests.png)