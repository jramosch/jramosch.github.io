---
layout: post
title:      "Sinatra Project: Travel Wish List App"
date:       2018-06-25 18:26:01 +0000
permalink:  sinatra_project_travel_wish_list_app
---


Having to balance freelance / temp work with my online courses with Flatiron has proven to be a particular challenge on its own. Planning for this project was essential to tracking progress, as my other responsibilities took me away from my coding studies. 

However, while progressing through this section, planning seemed more and more integral to the successful execution of the program. The entire Sinatra curriculum handles the structure of the CRUD app in sections, demonstrating the function of each part as it instructs you how to build it out.

## Building Blocks & Questions

While this can be said for every section, the importance of structure didn't feel as significant till this section (at least for me). Each section essentially covers one of the many building blocks to be used to construct the final project. 

This sort of instruction made me start pondering on my project in the same way - in parts. Conceptualizing the project begins with a simply question: "what will my app do?" 

Thinking along of something I have interest in, it began with the idea of traveling. What can one create related to travel? A list of destination for travel, aka a "wishlist". A list that will contain attractions, which take place in cities. 

Then it's a simple matter of reimagining or rephrasing the function of these things within the structure of a Sinatra app. A user `has_one` wishlist, which `has_many` attractions, which `belongs_to` a city (and user).

Continuing this thought process helps you plan out the file structure of your project. Following the MVC design pattern, which divides an app into three interconnected parts, one can build out the models, views, and controllers for each component in parallels.

## MVC Design & Structure

Establishing functions and relationships between models, gathering input from and presenting information to users via views, and using input to execute changes to your app's components via controllers. 

Understanding this structure of the Sinatra CRUD app made it that much easier to plan and develop the app. Finally, it's all a simple matter of ensuring all parts are performing their intended functions first on their own and then with one another. 

While the most legwork and perhaps the most tedious, actually building out the code becomes easier when the app's intended use is always in mind. Clear intention and structure are great tools for cutting through tedium and essential for the growth of any learning developer.
