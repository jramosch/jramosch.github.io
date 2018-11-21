---
layout: post
title:      "REWRITE: Rails MVC"
date:       2018-11-21 23:06:27 +0000
permalink:  rewrite_rails_mvc
---

###   *A small endeavor in rewriting the labs encountered during my Flatiron Education.*

Model-View-Controller (MVC) is a software architecture pattern commonly used to develop user interfaces, making it a popular choice for designing web applications. The pattern provides developers a way to separate concerns into three interconnected parts, usually separating internal logic from how information is presented to users. 

Following a specific set of conventions, application logic is managed by the **M**odels, content display by the **V**iews, and code flow by the **C**ontrollers. 

![src: sitepoint.com](https://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2017/10/1508423394rails-revealed_mvc-diagram.png)

#### Roles & Responsibilities

###### Model

The model is the central component of the MVC pattern, managing the data, logic, and rules of the application. Within Rails, the model is a Ruby class inheriting from the `ActiveRecord::Base`, meaning it has a corresponding database table and access to methods that aid in working with that database. 

Treating it like anyother Ruby class, you can create methods, data attributes, and any custom logic you'd like for your model. Just remember methods placed in a model file should be within the scope of that specific model. A typical model file will contain validations, database relationships, callbacks, etc.

Independent of the user interface, the model receives its user input via the controller.

###### View

The view defines how an app's data is presented. In Rails, the view contains the least amount of logic, as its role is to render whatever is received from the database (via the controller). 

Rails also provides built-in [ActionView helper methods](https://api.rubyonrails.org/v5.2.1/classes/ActionView/Helpers.html) you can use to code views efficiently. 

The below example (provided by Flatiron)...

```
<%= div_for(@post, class: "post-index-page") do %>
  <p><%= @post.title %> <%= @post.summary %></p>
<% end %>
```

...translates to the following HTML markup: 

```
<div id="post_42" class="post post-index-page">
  <p><strong>My Amazing Blog Post</strong> With an incredible summary</p>
</div>
```

The Action View helper (`div_for`) allowed us to dynamically set the HTML tag without actually writing any HTML code at all. As your views grow in size, you'll come to rely on such tools, because the more Ruby (and the less HTML) you use, the more manageable your views will be. 

###### Controller

The controller manages data flow between the models, views, and routes. Receiving input from app users, the controller converts that input into commands for the models and views. 

The view only has access to instance variables provided by the controller, which contains data from the database. The routes ensure the controller methods match items in the routes file. 

-------

#### Routing, File Naming Conventions, and Data Flow: Blog Example

![src: viblo.asia](https://viblo.asia/uploads/c73060bc-984a-40d1-bee0-8e7d73782e87.jpg)

At its core, Rails is focused on "convention over configuration" and this is no different for how it implements the MVC structure. As previously outlined, view files correspond directly to controller files, which speak directly with models. Using the same example provided by Flatiron - a blog that has a database table called posts - a quick ;

* A `post.rb` model file contains validations, database relationships, callbacks, and any custom logic for posts.

* A `posts_controller.rb `file has methods to manage data flow for the Post behavior, including the full set of CRUD features. Standard methods include `index`, `new`, `create`, `show`, `edit`, `update`, and `destroy`. 

* A `views/` directory contains a corresponding view for each page the end user will access. Following the CRUD model, a few standard views include: `index` view to show all records, `show` view to display a specific record, and `new` & `edit` views each rendering a form.
