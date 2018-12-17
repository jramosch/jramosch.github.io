---
layout: post
title:      "REWRITE: Rails Static Request"
date:       2018-12-17 23:06:57 +0000
permalink:  rewrite_rails_static_request
---

### Routing

Unlike most other languages, Ruby on Rails does not rely on the web server to control URL routing. Its routing system instead uses the routes file (`config/routes.rb`) to examine incoming URL requests and determine the controller actions responsible for handling each request.

Before we proceed, let's understand this routing flow at a higher level;

![source: medium](https://cdn-images-1.medium.com/max/800/1*KK61kGXrkaFBDfY7uWukyQ.png)

1. User submits an HTTP request by entering a URL into the browser
2. Upon receiving the request, the server interprets the it and sends a message to the *controller* mapped to the route
3. The *controller* communicates with the *view* file mapped in the *controller* method.
4. Finally, the server returns the HTTP responce contained within that view page

### Static vs Dynamic

Rails's comprehensive routing system expands well enough to handle both static and dynamic routes. Below are the definitions / differences between each;

* A **static route**, as its name implies, renders a view that does not change. Because of its unchanging nature, parameters are typically not sent to this type of route. Examples of this include a site's about or contact pages.

* A **dynamic route** is a page that accepts parameters, rendering content based on those parameters. Examples of this include a blog's post page containing a specific article or a individual's profile. 

### Implementing a Static Route

Working solely with static pages doesn't require any models to interface with a database, however, a controller is necessary. Using a blog application as an example, we simply create a controller to handle all static routes in the following directory: `app/controllers/static_controller.rb`. The controller should inherit from the application controller, to ensure access to the number of methods built into the Rails controller system. 

```
class StaticController < ApplicationController
end 
```

*NOTE: The standard naming convention for controllers is the name of the controller followed by the word Controller.*

Now we should include an action to handle the render of a static page. For this example, this can be the `about` action;

```
class StaticController < ApplicationController
  def about
  end
end
```

We'll now have to tell the `about` action to render a page template. Fortunately, Rails provides us with two options for mapping between the controller and view files;

* **Explicit rendering** allows you to specify a view file for the controller action to map to.
* **Implicit rendering**, following a standard convention, maps to a view file with the same name as the controller action.

Before proceeding with either option, we'll first need to create a `static` directory within the views directory, which will hold our static page views; `app/views/static`. 

To first demonstrate*explicit* rendering, we'll first create a view file withinthe newly created `static` directory; `app/views/static/some_page.html.erb`. We can now render this page in the `about` action either using the full view path (`render "static/some_page"`) or omitting the enclosing directory (`render "some_page"`). Rails automatically looks within the view directory of the same controller name. Typically, it's best pratice to use the latter `render "same_page"` syntax, as it doesn't rely on the directory name in case its name is changed. 

With all this in mind, we'll first add some content to our `some_page.html.erb` view;

`<h1> Greetings from some page! </h1>`

And we'll render this in the `about` action of our Static Controller;

```
class Static Controller < ApplicationController
  def about
	  render "some_page"
	end
end
```

Now to see how Rails utilizes implicit view rendering, we'll create a new view in the static views directory called `about.html.erb` with some HTML code;

`<h1> This is the about page! </h1>` 

And, after removing the `render` call, our `about` action will now route to the `about.html.erb` page. As previously described, *implicit rendering* follows the Rails pattern of 'convention over configuration' and only works due to Rails' numerous complex processes. 

It's best to utilize the implicit workflow and follow the standard conventions. Not only does this make the development process as efficient as possible, but also makes it more readable for any developers that may work on the application in the future. 

------

#### *Keywords;*

* ***Routing*** is the process of selecting a path for traffic in a network, or between or across multiple networks. Broadly, routing is performed in many types of networks, including circuit-switched networks, such as the public switched telephone network (PSTN), and computer networks, such as the Internet.

* ***URL Routing*** enables you to define URL mapping rules within your applications.

* ***HTTP*** (Hypertext Transfer Protocol) is an application protocol for distributed, collaborative, hypermedia information systems.

* ***HTTP Request*** is a packet of Information that one computer sends to another computer to communicate something.


