---
layout: post
title: "Generating Requirements"
description: ""
category: 
tags: []
---
{% include JB/setup %}
Now that you have seen some examples of what moving to a database backed system can do for you where do we go next?

If you have chosen your the form you want to start with the next step is to find out what type of data the various fields should use. These can be things like text, numerical values, dates, times true/false, yes/no, complete/not-complete, dropdowns for data that has a group of discrete choices, and so on.

The end result of this part of the process is going to be a list of data points and what type of data they contain. We will use that list to help design our database tables, but for now we are only interested in breaking the form down into its smallest components.

If your form can easily be divided into sections you will repeat this process for each section. If it is a simple form that is one section you can focus on the form as a whole. The example we will be working from is a form consisting of a handful of sections each with a different set of data requirements. You can start with any section of the form you would like as we will be tackling all of them as part of the process.

Choose part of your form and let’s get to it!

You will first want to break your form down into its component parts. The way I start is by looking at each section of the form as one whole unit. Typically each section is composed of similar types of data which may or may not be unique to that section. The form may have a header with a date, time, who is responsible for the work, a description and a status field. Below the header might be customer information, various tasks that need to be completed before work can proceed and below that might be quality control data with comments for things that aren’t as they should be.

Each of these sections will inform our database design in the next steps, and provide an easy way to find the relationships between data points that you will need to be aware of in the final product.

The process will go like this:
Go through a section of the form and find data that is useful on its own. (Date, description, file number, etc.)
From the remaining items break each section down into the smallest units possible. (Comments noted on the form throughout a shift are tied to the time they were written, your customer needs a name, address, email, phone, etc. which are all tied to the customer, etc.)
Make note of these items and the relationships between the data points.
Complete each section and compile your list for the entire form.

First we will start with data that is useful on its own, don’t worry about breaking things down too much or not enough, we will be verifying your list in the next steps:

The easiest data to start with is values that indicate dates and times. Without getting into detail about the actual data, find any values that are dates and times and enter the name of the items into your list. In a second column make a note for each item indicating if it is a date, a time or a date and time. If you have a hard copy of the form you can highlight or cross off these items to show that you have already addressed them. If you don’t have a hard copy no problem, just make a mental note of those items and continue on. An example of these items on your list would be:
	-Due Date on form header, date
	-Time form was received, time
	-Due date and time of shipment, date/time

The next step is to look for items such as comments, notes or anything else someone is free to enter text of their own choosing on your form. Typically these would be a description in the header, notes about how to get to a customer’s facility, etc. Make a note of these fields on your list and beside them make a note that they are text. Additionally, take note of the length of the text that is typical for each field. For example 

	-Description, text < 25 words
	-Shipping Instructions, text paragraph


After text you want to look for items that can be yes or no, complete or not-complete, true or false. These are typically things like has the customer signed off on this shipment, is this work complete, etc. Examples of this data on your list:

	-Shipment complete, T/F
	-Customer Approved, Y/N
	
Next you want to look for items that have more options than yes or no and have a list of standard choices. An example of this would be an item’s color which can be blue, green, red or yellow; or the condition of a part which can be new, used, or scrap. You can also include items that have “Other” as an option even if there is an option to enter a comment. We aren’t looking to design our database yet, just covering the bigger picture items. You also don’t need to write down the choices for each item, however you can if you wish. Examples:

	-Finish color, Multiple options
	-Part Condition, multiple options

The final item to look for in your first pass are numeric values. These might be a cost, estimated time to complete the work, number of units per order, etc. You want to capture that you have a numeric value and if the number needs to include decimal places, for example you might use 53.6 feet of wire in this product or if it is a whole number, for example you will ship 12 units per box but never 12.5. These aren’t hard and fast rules at this point, just a guideline for now:

	-Wire per product, decimal
	-Units per box, integer

Now that you have broken out the individual data points let now take a look at items that have multiple items for each unit. These are things like notes taken during a shift that include the time they were written down, a task that has an associated due date and also if it has been completed or if your quality control data has an associated date, time and product identifier.

These items will generally be a group of the previous types of data. For example you might have 20 different quality measurements that are taken every hour in which case you would make a note of the data type and how many data points there are. 

For each of these items it is easier to keep them on the list you have put together and instead of adding each one as another line, group them together like so:

	-Wire per product, decimal
	-Form Description, text <25 works

	-Shift status update, text <25 words
	-Shift status time, time
	-Shift Status personnel, full name

	-Quality data readings, decimal (x)20
	-Quality data date/time, Date/time
	-Quality Data product, text 16 characters

As you complete each of these items you can highlight or cross them off the form. 

Now that you have gone through one section of the form and made a list of the fields you want to capture, repeat the process for the rest of the sections on the form.

Once you have gone through all of the sections of your form your list should give you a complete picture of the fields you need to track in your database to replace your existing form.

Before we take your list and start designing the database you should put the list aside and think about the workflow you use in conjunction with your form. This doesn’t have to be super detailed, the idea is that you want to find any tasks that you can automate with the new system.

Questions to ask for some of the common tasks that can be automated are do you ever scan the form and email or store the document on your computer? Do you ever complete one section of the form and send it to someone else to complete the next section? Does anyone ever need to approve anything on your form before moving to a new step of the workflow? Do your customers ever see the form as part of your process? If so do you ever need to hide or change any sensitive information before the customer sees the form?

There are any number of potential tasks you can automate, these are just a few typical examples. Let’s walk through a couple of them to show the possibilities:

If you ever need to scan and email the form after you have filled it out you can save time by building this functionality into your system. The form you would normally scan will be replaced by your user interface and all of the data will be stored in your database. This process can be greatly simplified by adding a button to the page that generates a document and automatically emails it to whoever needs to see the form. You save time in printing the form, scanning it, finding the scanned file and attaching it as an email. You can also track the status of the form and see when it was sent out or if it hasn’t yet been sent.

Another powerful example of the new method is if you ever need to have someone approve the information on the form before moving to the next stage in your workflow. Let’s say your form is for tracking projected costs for buying office equipment. You need to compile a list of items with their associated costs and have your purchasing department approve the order before it gets placed. Normally you would need to put the form together, send it over to the purchasing department and follow-up with them until you get your response. You may have to make changes and repeat the process until everything is finalized and agreed upon.

In the new system you can simply update the form to the first stage of completion which would automatically email the specified people in the purchasing department. They then can login to the system and work off the same copy of the data you entered. If they have comments they can enter them directly into the system and notify you of the changes. If there are due dates for the process you can configure the system to end out updates to make sure nothing falls through the cracks. Once purchasing has completed their review they update the status to the next stage of completion and the next person in the process is notified that they have some pending action items.

This type of system makes it simple to track comments on the data, who entered what and when and doesn’t require you to dig through your inbox to find an email from a week or two ago that you didn’t have time to handle when it first arrived. This reduces the amount of time you spend dealing with process related issues, makes it easier to find and use the information you need to do your job and greatly simplifies the process of training new people as your company grows.

Think about some of your processes and ways that you can utilize the new system to automate tasks for you. Just about anything you do manually can be configured in the system and you can leverage things like email, file storage and notifications to simplify your workflow.

Add any items that can be automated to your list of data fields from your form and take a break. We will dive into using your list to develop a requirements list in the next steps. With those requirements you can bring your needs to the table when you look for someone to help you implement the new system and make sure you get everything you need.