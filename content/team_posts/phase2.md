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

## (Updated 6/15/25)

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
- ![First Page of Traveler Wireframe](F_Traveler_1.jpeg)
This is the first feature the user can encounter when signed in as the European Traveler. On this page, users can input their personal preferences such as prioritizing saving money, reducing travel time, or visiting popular destinations and receive a ranked list of countries based on those values

3. European Traveler Page 2
- ![Second Page of Traveler Wireframe](F_Traveler_2.jpeg)
This is the second feature the user can encounter when signed in as the European Traveler. On this page, the user can input the country they are visiting and a list of the top 5 attractions for that country will return. 

4. National Director of Tourism Page 1
- ![First Page of Director Wireframe](F_Official_1.jpeg)
This is the first feature the user can encounter when signed in as the Tourism Director. On this page, the user can select a country to compare their country of nationality to. These graphs can then be posted for the researchers to view and conduct their posts upon

5. National Director of Tourism Page 2
- ![Second Page of Director Wireframe](F_Official_2.jpeg)
This is the second feature the user can encounter when signed in as the National Director of Tourism. The user can view the data that impacts the future tourism prediction through various graphs. When the user firsts opens this page, only their country of nationality is selected in the model but the user is able to change how many countries they are viewing by clicking the countries on the side.

6. European Tourism Researcher Page 1
- ![First Page of Researcher Wireframe](F_Researcher_1.jpeg)
This is the first feature the user can encounter when signed in as the European European Tourism Researcher. On this page, the user can view existing posts from other researchers and they can aslo edit and delete their own posts but not other posts that are not created by them.

7. European Tourism Researcher Page 2
- ![Second Page of Researcher Wireframe](F_Researcher_2.jpeg)
This is the second feature the user can encounter when signed in as the European European Tourism Researcher. On this page, the user can create a post for each graph that is displayed (graphs will be displayed when the Official posts them). The user can create a post with a title and a content part.

<br>

## Global and Persona ER Models
<div style="width: 640px; height: 480px; margin: 10px; position: relative;"><iframe allowfullscreen frameborder="0" style="width:640px; height:480px" src="https://lucid.app/documents/embedded/b232c25c-6c0f-44d9-99cc-d8ebb671822c" id="rFzj1BL4b9vs"></iframe></div>
Use the cusor to zoom in/out or use the plus and minus sign (in order to see all the models).
<br>

## Inital MySQL DDL Model
![mySQL DDL inital code](NewMySQLDDL.png)
Here is the link the to code of the Inital MySQL DDL model <br> [Link to mySQL DDL Code ](https://drive.google.com/file/d/1ZFyc5f8cmMpUQ4mWYdywM4zaQxLdK5m2/view?usp=sharing)


## Data Visualizations & Reasoning

### Passenger Cars Data
{{< iframe src="cars_vs_year.html" width="150%" height="600" >}}

- The Passenger Cars data file provides extremely in-depth features, like type of motor engery and size of engine. By taking advantage of the ability to include all motor energies and engine sizes into a category called "Total", this allows for a more holistic analysis of these features and how they interact with time. The most prominent and simple interaction between features to observe in this case would be how the number of passenger cars increases with time. By choosing to implement a line graph with number of cars along the y-axis and years along the x-axis, it is easy to see how the number of cars has steadily increased across time. Observing this trend is not only important for supporting our inferences, but important with regards to coinciding with our user personas' goals dealing with gaining a general understanding of how number of passenger cars and year interact with each other. On a planning basis, it allows us to develop insights for how possible machine learning models might handle certain choices for features. 
- As an interactive feature, the user can go over to the legend of countries with their corresponding line color and toggle them on and off. When lines that are significantly above or below others are toggled off, the graph automatically zooms in to get a better view of the remaining lines. This makes it extremely useful to get a closer look at trends that are more difficult to observe, like the clustering of lines beneath leading countries in size, population and travel.

{{< iframe src="carspercap_vs_numcars_dot.html" width="150%" height="600" >}}

- Where Passenger Cars vs. Year gives us a very simple look at how the number of cars steadily increases as time goes forth, it does not factor in how certain countries, such as Spain, Germany, or France, will naturally have a high number of cars over time simply because they are larger in population size. In order to get a look at a more in-depth trend, we decided to create a new column of data that details the Number of Cars **per capita**. 
- This new feature was created by merging a dataframe from another file with details about GDP spending by country, and dividing number of passenger cars by the GDP for the corresponding country. Using this new feature in a line graph allows us to see how a country's GDP directly affects how passenger cars changes with time. 

{{< iframe src="carspercap_vs_year.html" width="150%" height="600" >}}

- After graphing number of cars per capita against number of cars, we can see that smaller countries like Bulgaria have jumped to the top of the graph. While initially seeming like a confusing correlation, this could demonstrate the ease for an individual to own more cars in areas with lesser prices. While this feature might be more difficult to obvserve in a meaningful way against other features with machine learning, especially with our rough plan to perform a time series linear regression, it is a good feature to observe now to strengthen our understanding of how features accross our datasets correlate to each other.
- Following the same idea with the number of cars vs. year graphs, we chose to make this scatterplot interactive in order to observe the strong trends that were difficult to observe due to higher countries on the plot. By removing the top few countries, the initially small trends that appear at the bright blue datapoints suddenly become much easier to see. Ultimatley, this is a method that both tests how we want users to interact with the visualizations to create a more personalized experience as well as being able to understand trends we are seeing. Without having a solid foundation of knowledge for how features can correlate to each other, it makes it more difficult for us to forsee how it would align with our users' goals.

### Number of Trips (Tourism) Data
{{< iframe src="trips_per_year.html" width="150%" height="600" >}}

- Adding in the Tourism Data was a little difficult considering how the data contained duplicate data for every year, leading to a longer and more hands-on process being required for for cleaning. Each visualization has been filtered to contain trips under the personal leisure category that last for 1 or more nights. By doing so, we thought this would allow us to capture the most accurate number of tourism trips for the most amount of nights in order to ensure the largest data pool for tourism possible.
- We started by observing the simple and more obvious features of number of tourism trips versus year. By first understanding this trend, it allows us to see if there is an observable correlation that could be useful for one of our machine learning models, like our early idea for a time series linear regression that could be used by our National Director of Tourism to increase their economic benefits from tourist trips in each country.
- This graph also features an interactive element, with the user being able to toggle on and off lines in order to better oberseve what is happening beneath a few higher-scale trends near the top of the graph.

{{< iframe src="trips_top_three.html" width="150%" height="600" >}}

- Since including every country on the simple line graph appeared to have overcluttered some possible trends, we decided to look at the relationship between just the top three countries in tourism to see just how much their magnitude differs from the other countries in this dataset. We filtered the data to return a list of the top three countries to make sure we had the right idea, and then created a new visualization for these.
- With the countries being Spain, France, and Germany, we decided a clean, stacked bar chart would be the most effective way to view these tourist superpowers alongside each other in a visually appealing manner. Users can toggle between which countries they would like to view, and although this visualization might not prove very useful in the final product of the application, it allows for a deeper inferential analysis of exactly how much tourism is influenced by other factors like population, size, and GDP.

### Road Density Data
{{< iframe src="road_density.html" width="150%" height="600" >}}

- We chose a funnel chart to represent the road density across countries because of how visually intuitive it is. The chart arranges countries from those with the least dense road networks at the top to the most dense at the bottom. This layout helps highlight major differences at a glance. For someone planning a trip, this type of chart can offer a quick way to spot which countries might have more congested road systems, potentially influencing travel choices.

### GDP and Road Spending Data 
{{< iframe src="gdp_vs_roadspending.html" width="150%" height="600" >}}

- Since the dataset included several key variables, we thought an interactive scatter plot would be the clearest way to break it down. On the x-axis, we placed each country’s GDP, while the y-axis shows how much they spend on their roads. We also sized the dots based on GDP, which makes it easier to visually compare the countries. To help viewers follow along, each country is shown in a different color and size depending on their GDP and roadspending, allowing patterns and outliers to stand out more clearly.
- These visualization features an interactive aspect, where the user can use the slider along the bottom to animate the changes in GDP and roadspending as the years move forward. This allows for a seamless and fun way to keep the user engaged with hands-on learning with a model that might be initially difficult to understand due to all the colors, sizes, and features in play.

### Country Priotization of Travel and Tourism Data 
{{< iframe src="tourism_priority.html" width="150%" height="600" >}}

- Our goal with this dataset was to make it easy to compare how each country’s prioritization of travel and tourism has changed over time. To do that, we used a bar chart with the prioritization scores (on a scale from 1 to 7) along the x-axis and the country names listed on the y-axis. Each year is represented by a different color within the bars, so viewers can quickly spot changes and trends. This kind of visual is especially useful for travelers who want to understand which countries are putting more emphasis on supporting tourism.
- Users can toggle on and off the years in order to get a look at two different years in comparison with each other, or even view a single year of their choice.
