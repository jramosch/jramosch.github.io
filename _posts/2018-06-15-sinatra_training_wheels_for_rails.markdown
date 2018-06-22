---
layout: post
title:      "Sinatra: Training Wheels for Rails"
date:       2018-06-15 09:42:56 -0400
permalink:  sinatra_training_wheels_for_rails
---


## Sinatra: "Yuck"
While at an on-campus study session, I recall telling one of the monitoring helpers that I was up to the Sinatra. To which he replied: "yuck"

As someone who hadn't reached the Rails section of the curriculum, the response did not yet resonate with me. But, as I understand it, Sinatra serves as the training wheels for Ruby on Rails. As a "*light weight* framework", Sinatra heavily relies on the developer for app structure and communication. 

While Rails probably streamlines this process, Sinatra allows for us budding new developers to really get our hands dirty and familiarize ourselves with MVC concepts. 

## MVC

Commonly used for developing software, model-view-controller (MVC) is a design pattern that divides an application into three interconnected parts: model, view, and controller. 

![](https://upload.wikimedia.org/wikipedia/commons/a/a0/MVC-Process.svg)


The model, responsible for managing the data of the application, functions as the central component of the pattern. 

The view is the presentation of the model in any particular format, such as a chart or diagram. 

The controller accepts user input and converts it to commands for the model or view. 

# The Most Basic of Basics

After ensuring Sinatra is installed, using 'gem install sinatra', you can create the following basic Sinatra app in the app.rb file:

    require 'sinatra'

    class App < Sinatra::Base
        
        get '/ do
            "Sinatra, why're you so basic?"
        end

    end

Running rackup app.rb will start the above web application and output some textual ramblings. However, you should pay close attention to the "Listening on" line, which will inform you what address to navigate to in order to see your running web app. 

For example:

    Listening on tcp://localhost:9292
    *navigate to http://localhost:9292*

    Listening on 192.241.134.186:30000
    *navigate to http://192.241.134.186:30000*

At any time, you can stop running your application by typing "Ctrl+C" in your terminal. 

While the above app structure is the most basic Sinatra app structure, it's rarely used. Most Sinatra apps have a modular structure encapsulated* by Controller Classes and booted via the config.ru Rack convention. 

# Keywords*

encapsulated (v. - *computing definition*) -- enclose (a message or signal) in a set of codes that allow use by or transfer through different computer systems or network
