---
title: "Project - Phase III"
date: 2025-06-05
draft: false
description: "Building functionality into our Project"
slug: "phase3post"
tags: ["project", "author"]
authors:
  - "aidankelly"
  - "seanbehan"
  - "gabbymontalvo"
  - "mariasamosrivas"
showAuthorsBadges: false
---

# Updates to Phase Two
While working through phase three, our group continued to develop how our user personas would interact with the app. We futher developed the researcher, who now will have a page to make research posts, a page to view the posts and a page to view trends between road saftey and tourism variables. These tourism variables includes passenger car data road quality and road density all on the country level. We also changed the ER relationship to limmit the scope of the reasearcher, include road death data and to merge all the new diagrams to the global ER diagram. This change also implies that we modified the mySQL database by adding new a new table for the RoadDeaths, for the Reseacher and the ResearchFindings. 

## Updating Maps
Updated visualizations from the number of passenger cars file and made visualizations for the number of trips per country data file. 

All these changes can be viewed on the phase two deliverable

 <br>

# Phase III Deliverable
The main focus of this phase of the project was implement the functionality via creating the API requests and creating the ML models. 

## Features Used in ML Models

### Fuel Price 
As the EU is so large with countries of varying economic circumstances, we thought it was in the best interest of our users to be able to plan ahead and input their preferences on fuel price in order to better suit their budget. Users can adjust the slider in the interface based on how important fuel spending is to them when considering their personal budget. 

### Traffic Density
Our inference for traffic density is based on the Road Density dataset, which shows the amount of cars in one kilometer over 100 km squared. Road density and traffic are important to our users, particularly to our European tourist persona, because ideally tourist would want to travel to areas with less traffic than others. This will minimize the time spent in the car and maximize the enjoyability of the journey, aligning with EuroTour's core values as delivering the smartest recommendations for each traveler. 

### Tourism Numbers
When saying "Tourism Numbers", we are referring to the Number of Trips taken to each country under the "Personal reason" category. While the dataset includes number of trips for "Professional/Work" reasons, we thought the best way to portray the amount of tourism for each country was to filter the dataframe to only include "Personal reason", because of the implication of taking a trip for leisure time. Including this feature is important for our Recommendation Model because each traveler is their own person, with their own unique preferences for how people-dense they want the area they visit to be. Some travelers might prefer to travel to a country with less or more dense tourist areas, hence their ability to adjust the slider in the direction they want towards more or less tourist heavy areas.

## Challenges When Building Model
After we started building the model, we encountered initial challenges like merging our two datafiles from MySQL, cleaning the data in ways like standardizing all features through min/max normalization, and going through trial and error to find the best way to mathematically calculate which five countries best suited the preferences of our user. Initially, we tried an idea with calculating the distance between the user's input and each country's vector, but ended up shifting our approach to cosine similarity as we learned in class for a cleaner, directional implementation. This required restructuring a few functions, but we ultimately accomplished building a model that gives our user recommendations based on their inputs, then connected the top five countries to be displayed on a density plotly express map. The user is then redirected to a page with their recommended countries, with the darkest countries being the most similar, and the lighter countries being less similar. Ultimately, working on the model was a great experience to not only implement what we learned in class, but to learn more about how to better work as a team to consider what would work best for our models.

## Streamlit App Functionality
![Ellie Landing Page](ellielandingpage.png)
- When signed in as Ellie, this is the landing page that it will take you to

</br>

![Ellie Post Request Page](ellieRequest.png)
- When signed in as Ellie and the user clicks the create post button, this is the page that will show up. The user can input a title and text regarding their research. Then when they are ready, they can sumbit and a POST request will add the input to the ResearchFindings Database in MySQL for the user to view.

</br>

![Ellie's Post](elliepost.png)
- When the user is signed in as Ellie and the user clicks the view posts button, this is the page that they will see. They can open the drop down menu and see the post that they have made. Since this is their post they can also edit it and delete it.

![Can't Edit](cantedit.png)
- Here the user is signed in as Ellie and this means that she can only edit and delete her own posts. If Ellie views other posts by other users, she cannot delete them, as seen by the lack of edit and delete buttons in the other post.

![Editing Post](editingpost.png)
- Here the user (who is signed in as Ellie) is editing her post. Once the submit button is pressed, it will sent a PUT request to change that row in the database with the new inputed values.

![Post has been edited](postisedited.png)
- Here the post that Ellie had made prior has been edited and now her changes be viewed. Her orignal post with her original content has been overiden by the PUT request by the user. If the user presses delete here, a DELETE request will be sent to delete that row from the database ResearchFindings and then that post will not be visable anymore. 
Like this.
- ![Post has been deleted](deleted.png)

![Traveler Home](travelerHome.png)
- Here is the landing page for the traveler after the user has signed in. Here the user can choose to decide where to travel and look at traffic prediction

![Travel Help](travelhelp.png)
- Here is the page that helps the traveler user plan on where to go. The user is able to slide the slider to the values that best represent their interests. The map at the bottom will highlight the top 5 countries they should plan a trip too based off their input.

![ML model working](ml-model.png)
-Here the recommendation ML model has output the top 5 countries that best fit the users input. The countries are highlighted on the map (darker being more likely to match the users desires and lighter being less likely). They are also listed at the bottom.

## REST API Matrix

1. POST Request for Researcher
When the user is signed in as the researcher and is on the create posts page, they have the ability to create a post with a title and body text. When the user presses submit, a streamlit form will send the data as JSON through the POST request that is embeded in the submit button. This POST request will add the text and the post content to the mySQL database and will store it for the user to view on the view posts page

2. GET Request for Researcher
When the user is signed in as the researcher and is on the view posts page, a GET request will be made to the mySQL database to retreive all the posts in the post ResearchFindings table and display it to the user. The user is able to see all the attributes of the post as it is stored in the database like time, title, content, post id, but not the author id only the author name for security purposes.

3. PUT Request for Researcher
When the user is signed in as the researcher and is on the view posts page, if they are on a post they have made, they can edit the existing post on the streamlit website. This will prompt the user to make the changes in a streamlit form and when they submit, will send a PUT request in order to edit the existing post in the database. This will then update the post in real time.

4. DELETE Request for Researcher
When the user is signed in as the researcher and is on the view posts page, if they are on a post they have made, they can delete the existing post on the website. This will send a DELETE request to the API and will then delete the specific row in the mySQL database under the ResearchFindings table. The user is unable to recover the posts after they are deleted so we should make sure the user knows this.

5. GET Request for Traveler
When the user is signed in as the traveler and is on the where to travel page, they are able to input their desired level values for travel time, cost, and tourism population. Since this is wrapped in a Streamlit Form, when the user submits, the values from the sliderbar are placed into the GET request to the API and those values from the request are used as the values to generate a ranking (from the recommendation ML model) of the top 5 countries that match the users input. The recommendation ML model rankings are then used to highlight on a map the top 5 countries.

6. Another GET Request for Traveler 
When the user is signed in as the traveler and is on the view travel data page, a GET request to the API will get the data from the mySQL table that is relevent to the country they are traveling in (via a dropdown selection) and it will display the data.

7. GET Request for Tourism Director
This endpoint uses time series modeling to forecast future tourism trends and visitor numbers. The predictions help tourism officials make strategic planning decisions and allocate resources effectively.


### Tourist API Resources
![Tourist Requests](touristRequests.png)
</br>

### Researcher API Resources
![posts Requests](postsRequests.png)
</br>

### Tourism Director API Resources
![official Requests](officalRequests.png)


