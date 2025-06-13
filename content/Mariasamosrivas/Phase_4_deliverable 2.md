---
title: "Phase 3 Deliverable"
date: 2025-06-13
draft: false
description: "Maria Samos Rivas phase 4 individual deliverable" 
slug: "samosrivas_maria_phase4"
tags: ["authors", "config", "docs"]
authors: 
  - "mariasamosrivas"
showAuthorBadges: false 
---

# Experiences and Lessons  

I can’t believe we’re leaving Belgium in less than 24 hours. These past four and a half weeks have flown by. It honestly feels like just yesterday we were sitting on the floor at the airport, waiting for everyone in DOC to arrive, and now we’re packing up to go home. We’ve seen so many new places (The Grande Place is still my favorite), met incredible people and speakers, and made some really special memories along the way.

This week, we also did a few fun activities that helped take the edge off all the work. My two favorites were the escape room and the soccer game. In the escape room, we had to work together as a team to save Ryan, we cracked codes, unlocked puzzles, and really leaned on each other to make it out. It was such a fun and bonding experience. We also went to see the Belgium National Team play, which was such a thrilling match. They played against Wales, and the game kept us on our toes right up until De Bruyne scored the winning goal in the 88th minute.

In the beginning, it felt like I was drowning in visualizations and endless data sourcing without really knowing what it was all for. But this week, everything finally clicked. Working on the ML models actually felt exciting because I could start to see the bigger picture and where it was all heading. That doesn’t mean it was easy, there were still plenty of late nights, stressful moments, and times I wanted to throw my overheated laptop across the room, but now, with just a few hours left until our final presentation, I’m genuinely proud of the work we’ve done.

I want to give a huge thank you to Dr. Gerber and Dr. Fontenot, especially Dr. Gerber, for being so patient with me. Whether it was when our time series model kept breaking or when I completely messed up the residual plot, thank you for sticking with us. I’m so grateful for the friendships I’ve made and everything I’ve learned on this trip. I hope next year’s DOC group gets at least half as lucky as we did.


## Here is a picture from our the soccer game! 
![Soccer Game](MariaSoccerGame.jpeg)

## Picture of the C-Mine!
![C Mine](MariaCMine.jpeg)


# Project Contributions 

This week, Gabby and I focused mostly on finishing up our first ML model and building out the second one, our time series model. After getting feedback from our last presentation, we knew we had a lot of work ahead of us. Since neither of us had ever built a time series model before, there was definitely a learning curve. We spent a lot of time choosing the right data, standardizing it, and figuring out how to structure the model itself.

Once we started building, we hit a bunch of roadblocks. We didn’t realize at first that with a time series model, you need to create lag columns for each year you're predicting, so when our model wouldn’t run, that was one of the key issues. That discovery meant we had to pivot from using multiple linear regression to just a single regression model. It was frustrating at times, but with a lot of help from Dr. Gerber and Sydney, we managed to get it working and ended up with a three-year prediction model which we were able to implement to the website. I also spent time on some last-minute refinements, building new visualizations and double-checking that our ML model met all the supervised linearity assumptions.
