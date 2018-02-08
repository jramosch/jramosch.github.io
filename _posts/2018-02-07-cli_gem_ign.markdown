---
layout: post
title:      "CLI Gem: IGN"
date:       2018-02-08 01:29:27 +0000
permalink:  cli_gem_ign
---


Initially wathching the Daily-Deals walkthrough, the CLI gem seemed a simple enough project. Pick a site, make a scraper for it, and create a CLI that allows the user to interact with the scraped data. Having done something rather similar in previous labs, albeit with a basic structure already intact, it didn't seem a huge leap.

However, I bumped into my first challenge upon selecting a site to work with. Initially, I wanted to create a gem that would be able to reproduce the schedule from my favorite programming block, Adult Swim. It didn't become clear to me that this wasn't a good pick until I was scrolling through the html of the site. Upon inspection, I realized the site had a lot of scripts, allowing it to be a pretty responsive website for users. But I wasn't entirely sure how to handle that issue of scrolling through different dates. Accessing information from this site was proving more difficult than anticipated and, unfortunately, the Daily-Deals walkthrough and Google wasn't providing answers in how to quite handle this problem. 

While I didn't anticipate this hiccup, it's always good to have backups in mind and my first runner up was IGN's website, which proved much easier to work with and covered another one of my favorite topics: video games. 

WIth a site selected and taking cues from the Daily-Deals walkthrough, I began with planning out my structure in a NOTES document. Something very basic that would be a little more fleshed out as I progressed through my project. I absolutely loved this tip from the walkthrough and found it extremely helpful. In general, planning out a basic structure always helps, sometimes even drawing on a piece of paper helps with visualizing a structure. 

Part of that basic structure building required a strong familiarity with the site. Although studying the site isn't entirely necessary to guess that each game should be an object, it certainly helped and it ultimately was needed to determine a game's attributes.  This meant creating a Game class with attributes identified from the site, which indlued a name, genre, platform, rating, url, and release date. 

Each of these attributes would be scraped from the site directly, upon creation of each game object.  In order to keep track of each new game, upon initialization, each game is collected in class variables, which are accessible from other classes. With the Game class using the methods of Scraper, the CLI class only needs to access the Game class methods in order to function. 

Throughout this project I was continually testing the CLI, using pry of course, in order to better understand the interactions and relationships between these classes, as well as improving upon the interface. As I encountered an error, loop or issue, I treated each solution as one as a marker for when to push changes to GitHub. Although, I'll admit, this was not a habit I picked up right away and it took some disciplined practice to get the hang of. 

Considering this is my first major project, I decided to keep this relatively straightforward and simply allowed users options on how they wanted to select a game and provide them access to the website's review itself (via the url). I gave myself a little more work by providing the user with more options in how they select a game, but the interface is ultimately still very simple. 

This project definitely gave me a lot of leeway in how to design, which was fun to work through. Ultimately I enjoyed the experience of building out a gem from top to bottom and believe I understand the structure of programs a little better. Hopefully I can continue to build upon those skills and make something more sophisticated in the near future. 
