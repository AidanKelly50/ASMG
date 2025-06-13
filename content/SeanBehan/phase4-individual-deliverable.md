---
title: "Phase 4 - Individual Deliverable"
date: 2025-06-13
draft: false
description: "Interesting things that I have learned on the fourth week of the dialogue."
slug: "phase4_ind_dev"  # if you use, needs to be different for every post
tags: ["authors", "config", "docs"]
authors:
  - "seanbehan"
showAuthorsBadges: false
---

# Phase Four Contributions

For phase 4, I was mainly responsible for three things, verifing/finalizing the origanization of the API requests/routes, implementing the unsupervised timeseries model into streamlit, and also styling the website to align with our app. For the first aspect that I did this phase, I ensured that the route names were not verbs and if they were, I changed them to only a noun and added mutliple methods to the route. Additonally, I had to create new routes and GET requests for the timeseries model so the predicted and historical data could be viewed on the graph. 

I also implemented the time series model into the predict tourism page that allows tourism officials to compare tourism data between two countries by fetching historical and prediction data from my backend APIs and displaying them in interactive Plotly graphs. I implemented a dual country comparison system that shows historical data as solid lines and predictions as dashed lines, with different colors for each country and statistical summaries including averages, peaks, and totals. I added comparative analysis features that automatically determine which country leads in different metrics and display winner indicators. Also, I created a POST request that lets officials save their graph comparisons to a MySQL database with custom names, storing the complete datasets as JSON so researchers can later view and analyze the saved comparisons.

I also was responsible for styling the overall page, utilizing CSS and streamlit functions to make the page seem more interactive depending on the user. The Official has a more well official and professional look, similar to the researcher and the traveler has a more welcoming and friendly.

# Interesting Aspects of the Dialogue for Week Four

I can’t believe that we are done with the dialouge. All the work that we have put in for the project has really paid off. Out of any class within Northeastern, I don't think I have learned more than I have in this class. I feel like in only 30 days I gained signifigant knowledge of MySQL, Python, CSS, Streamlit, Databases, Git Hub, Git, etc. Everyone that I have met on this dialouge has signifigantly impacted my postive expierence here and I will always treasure my expierence in Belgium.