---
title: "Project - Phase II"
date: 2025-05-27
draft: false
description: "Building the foundation to our project"
slug: "phase2post"
tags: ["project", "author"]
authors:
  - "aidankelly"
  - "seanbehan"
  - "gabbymontalvo"
  - "mariasamosrivas"
showAuthorsBadges: false
---

# Updates to Phase One
Through the duration of Phase two our team realized that with our initial design, users would all be using the app in a very similar way that made each persona seem irrelevant to how they were interacting with the data. Understanding this, we decided to pivot our idea to surround European tourism. Specifically we were focusing on creating an data driven european tourism app in which each user would interact with the app uniquely. With this new app, we had to also rethink our personas as how they would interact with this new app was different than our old personas. These new personas are similar to the other ones but their goals and wants that the app must satisfy differs to the older personas. 

## New User Personas

### European Traveler (Jacques Bon-voyage)
### National Director of Tourism (Nina Petek)
### European Tourism Researcher (Ellie Willems)

## Updates to Datasets
Since our focus for the project went from road deaths/road saftey to developing a data driven driven european tourism platform, the data also needed to change. In light of this, our group found a variety of new data for road congestion (number of cars on road), road spending by GDP, average fuel price, and tourism participation. These new data sets allow us to develop the tourism driven app around the 3 personas while also being unique to the 3 of them. 

These changes can be viewed in more detail in the phase one deliverable <br>

# Phase II Deliverable
The main focus of this phase of the project was to thoughtfully explore potential features that could be implemented in the app, based on the cleaned data and the data models developed by our group.

## Wireframing of EuroTour
Our team created wireframes to visualize what we envisioned the app would look like by the end of the development process, based on the available data and the features required to meet user needs and project requirements. Each wireframe page is a page that would be displayed on the app with the user interface displayed

1. Home Page
- ![Home Page of Wireframe](HomePage.JPG)
<br>
This is the base page where all users will see when the application is first opened up. This is the default page and the login screen

2. European Traveler Page 1
- ![First Page of Traveler Wireframe](TravelerPage1.JPG)
This is the first feature the user can encounter when signed in as the European Traveler. On this page, users can input their personal preferences such as prioritizing saving money, reducing travel time, or visiting popular destinations and receive a ranked list of countries based on those values

3. European Traveler Page 2
- ![Second Page of Traveler Wireframe](TravelerPage2.JPG)
This is the third feature the user can encounter when signed in as the European Traveler. On this page, the user can input the country they are visiting, the start and end date of their trip, and their prefered travel time (day/evening/night) and recieve a traffic prediction (time estimation).

4. National Director of Tourism Page 1
- ![First Page of Director Wireframe](DirectorPage1.JPG)
This is the first feature the user can encounter when signed in as the National Director of Tourism. On this page, the user can select a country, input a start and end date and recieve a double-lined trend chart of tourist numbers and GDP spending in correlation with the years range

5. National Director of Tourism Page 2
- ![Second Page of Director Wireframe](DirectorPage2.JPG)
This is the second feature the user can encounter when signed in as the National Director of Tourism. On this page, the user can select from a multi-select box—choosing factors such as fuel prices, traffic levels, or road density. They must also specify a year and set the desired increase or decrease in GDP spending. This input will generate an interactive heat map that visualizes the projected impact of these changes on the country level by color.

6. European Tourism Researcher Page 1
- ![First Page of Researcher Wireframe](ResearcherPage1.JPG)
This is the first feature the user can encounter when signed in as the European European Tourism Researcher. On this page, the user can select which data they would like to download from the various data sets used on the websites. They can choose if they want all the data, the date range of the data, the country(s) of the data and then can download the data.

7. European Tourism Researcher Page 2
- ![Second Page of Researcher Wireframe](ResearcherPage2.JPG)
This is the second feature the user can encounter when signed in as the European European Tourism Researcher. On this page, the user can write notes about the research they are able to conduct on they app and also upload pictures to their note page. The note page will be given an auto generated tag at the top for filtering purposes.

<br>

## Global and Persona ER Models
<div style="width: 640px; height: 480px; margin: 10px; position: relative;"><iframe allowfullscreen frameborder="0" style="width:640px; height:480px" src="https://lucid.app/documents/embedded/b232c25c-6c0f-44d9-99cc-d8ebb671822c" id="rFzj1BL4b9vs"></iframe></div>
Use the cusor to zoom in/out or use the plus and minus sign (in order to see all the models). For clearity, the researcher is the same as the Global data model as the researcher can view all the data for a variety of her studies 
<br>

## Inital MySQL DDL Model
![mySQL DDL inital code](mySQLDDL.png)
Here is the link the to code of the Inital MySQL DDL model <br> [Link to mySQL DDL Code ](https://drive.google.com/file/d/1dUJhlQq0w4GWwUo47a5TZEtMl-E3PAmh/view?usp=sharing)


## Passenger Cars Present in Europe Over Time - Data Visualizations
![numberofcars_vs_year](numcars_vs_year.png)
Explanation of Choices:
The Passenger Cars data file provides extremely in-depth features, like type of motor engery and size of engine. By taking advantage of the ability to include all motor energies and engine sizes into a category called "Total", this allows for a more holistic analysis of these features and how they interact with time. The most prominent and simple interaction between features to observe in this case would be how the number of passenger cars increases with time. By choosing to implement a line graph with number of cars along the y-axis and years along the x-axis, it is easy to see how the number of cars has steadily increased across time. Observing this trend is not only important for supporting our inferences, but important with regards to coinciding with our user personas' goals dealing with gaining a general understanding of how number of passenger cars and year interact with each other. On a planning basis, it allows us to develop insights for how possible machine learning models might handle certain choices for features.


![numberofcars_vs_year_zoom](numcars_vs_year_zoom.png)
Explanation of Choices:
The second visualization above is an example of an interactive feature implemented in the Passenger Cars vs. Year line graph prior to it. The user can go over to the legend of countries with their corresponding line color and toggle them on and off. When lines that are significantly above or below others are toggled off, the graph automatically zooms in to get a better view of the remaining lines. This makes it extremely useful to get a closer look at trends that are more difficult to observe, like the clustering of lines beneath leading countries in size, population and travel. In the example above, countries with these such qualities like Spain, France, Germany, Italy, and Poland have been toggled off. What remains is the lines above, which reveal a more observable pattern than there previously.

![cars_percapita_vs_year](numcars_percap_vs_year.png)
Explanation of Choices:
Where Passenger Cars vs. Year gives us a very simple look at how the number of cars steadily increases as time goes forth, it does not factor in how certain countries, such as Spain, Germany, or France, will naturally have a high number of cars over time simply because they are larger in population size. In order to get a look at a more in-depth trend, we decided to create a new column of data that details the Number of Cars **per capita**. This new feature was created by merging a dataframe from another file with details about GDP spending by country, and dividing number of passenger cars by the GDP for the corresponding country. Using this new feature in a line graph allows us to see how a country's GDP directly affects how passenger cars changes with time. 

![carspercapita_vs_number_of_cars](carspercap_vs_numdot.png)
Explanation of Choices:
- After graphing number of cars per capita against number of cars, we can see that smaller countries like Bulgaria have jumped to the top of the graph. While initially seeming like a confusing correlation, this could demonstrate the ease for an individual to own more cars in areas with lesser prices. While this feature might be more difficult to obvserve in a meaningful way against other features with machine learning, especially with our rough plan to perform a time series linear regression, it is a good feature to observe now to strengthen our understanding of how features accross our datasets correlate to each other.

![carspercapita_vs_number_of_cars_zoom](carspercap_vs_numcarszoom.png)
Explanation of Choices:
Following the same idea with the number of cars vs. year graphs, we chose to make this scatterplot interactive in order to observe the strong trends that were difficult to observe due to higher countries on the plot. By removing the top few countries, the initially small trends that appear at the bright blue datapoints suddenly become much easier to see. Ultimatley, this is a method that both tests how we want users to interact with the visualizations to create a more personalized experience as well as being able to understand trends we are seeing. Without having a solid foundation of knowledge for how features can correlate to each other, it makes it more difficult for us to forsee how it would align with our users' goals.

## Reasoning For Data Visualization

### Road Density Data
![road density picture](road_density.png)
We chose a funnel chart to represent the road density across countries because of how visually intuitive it is. The chart arranges countries from those with the least dense road networks at the top to the most dense at the bottom. This layout helps highlight major differences at a glance. For someone planning a trip, this type of chart can offer a quick way to spot which countries might have more congested road systems, potentially influencing travel choices.

### GDP and Road Spending Data 
![gdp vs road spending graph](GDP_vs_Road_Spending_per_country.png)
Since the dataset included several key variables, we thought an interactive scatter plot would be the clearest way to break it down. On the x-axis, we placed each country’s GDP, while the y-axis shows how much they spend on their roads. We also sized the dots based on GDP, which makes it easier to visually compare the countries. To help viewers follow along, each country is shown in a different color, allowing patterns and outliers to stand out more clearly as they move the bar at the bottom signaling the years.

### Country Priotization of Travel and Tourism Data 
![Country Priotization of Travel and Tourism](Country_Priotization_of_Travel_and_Tourism_Score_(1-7).png)
Our goal with this dataset was to make it easy to compare how each country’s prioritization of travel and tourism has changed over time. To do that, we used a bar chart with the prioritization scores (on a scale from 1 to 7) along the x-axis and the country names listed on the y-axis. Each year is represented by a different color within the bars, so viewers can quickly spot changes and trends. This kind of visual is especially useful for travelers who want to understand which countries are putting more emphasis on supporting tourism.
