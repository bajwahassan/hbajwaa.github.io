---
layout: post
title:      "CLI PROJECT"
date:       2020-03-28 12:44:09 -0400
permalink:  cli_project
---


Originally I wanted to build this project on an API because scrapping is simply too much work, and not very reliable if the site is redesigned. Anyway,  each API I liked was not free so I went for scrapping.

My Cli application is based on a site which keeps track of the world population, based on different categories. 
The first thing I did was making the interface, how will the user interface be. I wrote down all the options and sub-options a user will be able to choose from.

This application has five main options, where each option results in more options and then displaying data. A user can choose to get information on the top 20 counties with the most population. A user can also find future and past trends of the world population. some other options to choose from are by region, sub-region and by religion.

All the data that will be displayed to the user is scraped from the website and is initialized in a class to keep track of it. After data has been displayed to the user, the classes are cleared for the past data, because we don't want to keep that data.

I build the project, option by option, I worked on the first user choice, then the second and rest. This helped me to keep track of bugs, and not make things hard to keep track of. 
 
 After building all the user options, I implemented the QUIT option where the user can type 'exit' anytime to quit the application. Then I dried up my code, to be more specific, I created a module where classes shared the same behavior, I also created a parent class 'Region' where sub-regions will inherit its methods and functionalities. I also discovered the repetitive code in the 'Scrapper' class, so I build another method that will be responsible for scraping.
 
 When testing the application for all the given options, I was able to find another bug. The problem was if a user chooses to get more information (not just once), previous data would also be displayed as it was already stored. So I implemented another option wish will clear each time right away after data has been displayed.

As for now, the application seems to be bug-free. I will be adding more features to the application occasionally.


