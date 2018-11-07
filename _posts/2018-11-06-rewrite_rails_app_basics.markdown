---
layout: post
title:      "REWRITE: Rails App Basics"
date:       2018-11-07 04:45:02 +0000
permalink:  rewrite_rails_app_basics
---

###   *A small endeavor in rewriting the labs encountered during my Flatiron Education.*

Initially created in the 2000s, Ruby on Rails (or Rails for short) is a web application framework written in the Ruby language. A **web framework**, such as Rails, streamlines the process of building a web app.  While each web app has their own unique functionality, a web framework provides you with the baseline tools necessary to simply build one. 

Essentially, Rails is a set of Ruby code libraries - **a Ruby Gem** - and is opensource, meaning you can review the framework at any time to better understand how it works. 

Actually you'll notice a pattern, as Rails utilizes the **Model-View-Controller (MVC) framework**. The MVC framework encourages a set of app structure conventions, aiding developers organize and separate concerns.

-------

#### Installing the Rails Gem for Local Users

`gem install rails`

*May need to use `sudo` to install gem as the root user, depending on your system configuration.*

#### Generating a New Rails App

`rails new app-name`

*Creates a rail app called `app-name`, following the standard naming convention of using all lower case letters and separting by '-'.*

-------

## Rails File Structure Overview

* **app** - most of your app-specific code including the core three sections containing the models, views, and controllers. Most work will be done here. 

* **bin** - built-in Rails tasks you'll most likely never have to work with.

* **config** - manages a number of settings controlling the app's default behavior, including: environment settings, a set of modules initialized upong the start of the app, the ability to set language values, the application settings, the database settings, the application routes, and the secret key base.

* **db** - all database related files reside here; the configuration, schema, and migration files, along with any seed files.

*  **lib** - this directoy has all app-specific libraries, which are re-usable generic code extracted from the application. Think of it as an application specific gem.

*  **log** - stores log files, which can aid in debugging. Rails creates log files for each environment. 

*  **public** - holds common files for web apps, such as http error files such as 404, 422, and 500.

*  **test** - holds all test files for the app; a subdirectory is creted for each component's test files

*  **tmp** - temporary directory holding files like caches. This is full managed by Rails itself, but [there are commands available](http://edgeguides.rubyonrails.org/command_line.html#tmp) if you want to take controle of the directory. 

*  **vendor** - vendor files, such as javascript libraries and CSS files, reside here and automatically becomes part of the asset pipeline once filed here.

*  **Gemfile** - contains all gems included in the app. After any change, you'll nee dto run `bundle`. They're simply Ruby files that extend the app's functionality. 

*  **Gemfile.lock** - displays all dependencies each Gem has, along with their associated versions. This file should NOT be edited, as it can lead to application bugs. 

*  **README.rdoc** - document all application details here and any instructions to other developers you may have, such as how to run the app locally

-------

#### Creating the database

`rake db:create`

#### Starting up the Rails Server

` rails s`

*In order to **shutdown** the server, hit the `CTRL+C` button combination.*

#### The Rails Console

`rails c`

*Starts the Rails console, which gives you a direct conection to your app's ecosystem and lets you perform tasks such as: running database queries, running application code, performing full CRUD tasks with the database, and testing scripts in a sandbox mode.*
