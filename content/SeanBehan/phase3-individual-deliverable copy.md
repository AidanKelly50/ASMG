---
title: "Phase 3 - Individual Deliverable"
date: 2025-06-05
draft: false
description: "Interesting things that I have learned on the third week of the dialogue."
slug: "phase3_ind_dev"  # if you use, needs to be different for every post
tags: ["authors", "config", "docs"]
authors:
  - "seanbehan"
showAuthorsBadges: false
---

# Phase Three Contributions

For phase 3, I was responsible for developing the researcher user persona page. I created a researcher blueprint to access the API requests like GET, POST, PUT, and DELETE. The researcher was able to create posts that would use a POST request to update the MySQL database with the new row in the Research findings table. I also implemented the GET request, which the user was able to activate when they went to the View Posts tab. This feature allowed the user to see all of the existing posts that were in the MySQL database, including their own and others. For posts that were made by the user (did this through having the session state store the author ID upon sign-in), they can edit their existing posts and submit the changes by sending a PUT request, which will change the row of that data in the database to the new JSON data given by the user. 

On top of these routes, I also formatted the home page, the researcher pages, and attempted to fix all of the template pages to ones that will match our project (some are still in there for reference later).  I also added a new RoadDeaths table within the MySQL database, and generated mock data for the researcher to see posts by other users (and not edit them/ delete them since their user IDs don’t match), and I also fixed our ER diagram from the last phase.

# Interesting Aspects of the Dialogue for Week Three

I can’t believe that we are almost done with this dialogue. I feel like I have learned so much already, more so than I would have learned in a semester-long class. The project and all the class material really started to merge together for me, and I finally started to feel like I was gaining substantive knowledge in the larger CS world. All of the friends and experiences I have had on this dialogue have been unforgettable and definitely a highlight in my life.