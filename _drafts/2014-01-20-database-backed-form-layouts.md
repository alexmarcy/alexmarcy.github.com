---
layout: post
title: "Database Backed Form Layouts"
description: ""
category: 
tags: []
---
{% include JB/setup %}
One thing to consider when building a new system is the ability to easily add or modify items to your form.

Imagine you have a kiosk-based menu that lets people pick all of the items they want on their hamburger. Maybe your prices at lunch are different than at dinner because you are serving a smaller portion or you have some seasonal ingredients that you want to have on the menu this month and will take off next month when the supply runs out. How do you handle either of these scenarios?

The different prices for lunch and dinner could be solved by bringing up a different version of the form depending on the time of day. In the afternoon you show the lunch form with lower prices and in the evening you show the dinner form. That is one way to solve that issue.

To solve the seasonal ingredients scenario you can get more involved in the up front design to make your day-to-day life easier. Instead of designing a form that requires you to modify the layout anytime you want to make a change you can use your database to store some of the forms’ contents and make adjustments by entering or changing the data.

In this case you will have various sections of the menu for each type of ingredient, cheese, vegetables, sauces, buns, etc. In your database you will have some tables that hold the data to make up each section when the form is loaded. For the sake of our example imagine it is summer time and mangoes are looking really good at the farmer’s market. You put together an amazing mango chutney to add to your sauce options. To add it to the menu you simply open up your administration page, create a new entry of Mango Chutney, add any descriptions and the price and save it to the database.

The next time you load your menu the mango chutney shows up and all it took was a minute of your time to add. When the mangoes aren’t looking too great you simply open the admin page and delete the entry. Was a great seller that you want to do again next year? You could leave the mango chutney in the database and set it to inactive and save yourself a few minutes next summer. Contrast this with having to open the form, copy and paste the BBQ sauce line, change the text and price to Mango Chutney and then go in and delete the entry when the mangoes are out of season.

The seasonal ingredients scenario is similar to a lot of business applications. You add a new product line, a new process to your plant or a new position that needs to approve a part of the forms’ workflow. Instead of making changes to the form itself you simply add some data to the database. This not only reduces the amount of time you need to spend when making changes, it also gives you greater control to mange your processes yourself without the aid of any developers.