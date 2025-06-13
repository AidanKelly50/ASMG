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

## (Updated 6/13/25)
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
After we started building the model, we encountered initial challenges like merging our two datafiles from MySQL, cleaning the data in ways like standardizing all features through min/max normalization, and going through trial and error to find the best way to mathematically calculate which five countries best suited the preferences of our user. Min/max normalization was chosen due to its ability to be more flexible and sensitive to outliers, which was more than possible with our data containing varying values that would depend on the country's size and population as well. Initially, we tried an idea with calculating the distance between the user's input and each country's vector, but ended up shifting our approach to cosine similarity as we learned in class for a cleaner, directional implementation. This required restructuring a few functions, but we ultimately accomplished building a model that gives our user recommendations based on their inputs, then connected the top five countries to be displayed on a density plotly express map. The user is then redirected to a page with their recommended countries, with the darkest countries being the most similar, and the lighter countries being less similar. Ultimately, working on the model was a great experience to not only implement what we learned in class, but to learn more about how to better work as a team to consider what would work best for our models.

## Streamlit App Functionality
![EuroTour HomePage](EuroTourHomePage.png)
- When the user first opens the app, they will be able to sign in as 1 of 3 personas. Either the Traveler, the Tourism Director, or the Researcher. Each user displayed is a button that the user can login as and these names are retrived from the Users table in MySQL via a GET request.

</br>

![Official Model One](OfficialModelPage1.png)
- When signed in as a Tourism Director and viewing the Tourism Prediction Page, the user is able to compare their country that they are from (determined from the Users Nationailty in the Users table of MySQL) and compare it with any other country in the E.U. The graph plots both historical and predicted data of tourism numbers and the prediction comes from the supervised time series model. There is a GET request to view the graph with both countries and this get request pulls from the transactional table that stores the weights of each country. Officials can also post these graphs so the Researchers can view which is a POST request to the GraphFindings table in MySQL.

</br>

![View Tourism Factors](ViewTourismFactors.png)
- When signed in as a Tourism Director and viewing the Tourism Analytics page, the user can view the data that impacts the future tourism prediction through various graphs. When the user firsts opens this page, only their country of nationality is selected in the model but the user is able to change how many countries they are viewing by clicking the countries on the side. This is 4 individual GET requests to the MySQL database for the trips table, road quality, tourism prioritization, and road spending.

![Recomender Model ](RecommenderModel.png)
- When the user is signed in as a Traveler and viewing the where to travel page, they are able to generate the top 5 countries that best fit their input to 3 questions on a scale of 1 to 10. How important is saving money on fuel/travel cost? How much do you value avoiding long travel times/traffic? How important is it to visit high tourism areas? Based on these values, the cosine singularity between the values of the user and the values of each country will be taken via a GET request. Based on this difference, the model will provide the top 5 countries that are closest to 1 based on the values that the user inputted. 

![Attractions Page](AttractionsPage.png)
- When the user is signed in as a Traveler and viewing the Attractions page, they are prompted to select a country that they wish to view the attractions. When the Traveler selects a country, a GET reuqest is sent with that country to the MySQL database and retreives all the attractions under that country name. They are then displayed to the user with their specific town/city and also an external website to learn more about the attraction

![ViewGraphPostsPage](ViewGraphPostsPage.png)
- When the user is singed in as a Researcher and on the View Graphs page, they are able to see all the graphs that any Tourism Director from any country has posted. This is done via a GET request to the MySQL data base by taking all the rows in the GraphFindings table and displaying them. The Researcher also has the option to create a post about that graph underneath, allowing them to title the post and write a few setances about their findings. When they are ready, they can submit their post and this will trigger a POST request to add the new post to the ResearchFindings table for herself and other Researchers to view.


![ViewingAndEditingPosts](ViewingAndEditingPosts.png)
- When the user is signed in as a Researcher and on the View Posts page, they are able to see all of the other Researcher posts including their own which is done via a GET reuqest to the ResearchFindings Table in MySQL. Researchers are able to edit a post only if they were the ones that created it. As shown here, when logged in as Ellie Willems, the user can edit her own posts but not the posts of others (this is done by comparing st.sessionState UserID with the post Ids) Editing a post is the same format as Posting a new post in terms of the UI but behind the scenes, when the user submits the edit request, it sends a PUT request to edit that row in the Research findings table where that PostID is equal to edited one. Additonally, Researchers can also delete their posts and their posts only which is also done with the session state variable. When the user submits the delete request, that row in the MySQL table in ResearchFindings where the PostID is equal to the deletion will be deleted from the database and no longer able to view.

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
When the user is signed in as the traveler and is on the view tourist attractions page, a GET request to the API will get the data from the mySQL table that is relevent to the country they are traveling in (via a dropdown selection) and it will display all the attractions with the city/town and an external website that will inform the user more of the attraction.

7. GET Request for Tourism Director
The Tourism Director has 4 GET request to 4 unique tables in the MySQL database to display them to the user. The GET requests pull the data from the Trips, Road Quality, Road Spending and Trips Prioritization tables for the official to view either their countries data or as many countries as they have selected.

8. Another GET Request for Tourism Director
The Tourism Director also has a GET request which is given the country the time series model will predict upon and the country of nationality of the user. These two inputs will allow the graph to get two prediction values along with historical values that are being pull from the Trips table. To the user it is displayed as a two distinct colored lines on the graph.

9. POST Request for Tourism Director
The Tourism Director has a POST request which allows the user to post the comparison graph that they had created via the GET request above. POSTing this graph will then insert the data into the GraphFindings table in MySQL to be retreived for future viewing by the researcher.

10. GET Request for All Personas
When the user first opens the page, they are prompted to sign in as one of three personas. If the user clicks the dropdown menu, they are allowed to sign in as 5 distinct users which are all retrived via a GET request to all the users of type Traveler, Official or Researcher.



### Tourist API Resources
![Tourist Requests](touristRequests.png)
</br>

### Researcher API Resources
![posts Requests](postsRequests.png)
</br>

### Tourism Director API Resources
![official Requests](OfficialAPINew.png)


