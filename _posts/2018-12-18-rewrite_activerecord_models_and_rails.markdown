---
layout: post
title:      "REWRITE: ActiveRecord Models and Rails"
date:       2018-12-18 16:52:21 -0500
permalink:  rewrite_activerecord_models_and_rails
---


Rails, which is actually several Ruby gems working together, utilizes the Active Record as its built-in Object-Relational-Mapping (ORM). This enables your application to interact with data stored in your dtabase as though it was a normal Ruby object. Meaning you can manage data in a method driven stucture such as running queries, adding records, and other traditional database processes instead of writing SQL manually. 

For example, the traditional way to query a database of 'posts' using SQL: 

`SELECT * FROM posts`

Versus using Active Record:

`Post.all`

Using Active Record gives you access to advanced query tasks, such as method chaining and scoping, which typically require less code and make for a more readable query.

### Active Record Models

While a database table stores data, model files allow us to acess and interact with this stored data. The model file inherits from the `ActiveRecord::Base`, providing access to methods that allow us to work with the database such as `all`, `find`, `create`, etc. However, at the end of the day, the model file is a Ruby class meaning you can create methods, data attributes, and anything else you'd want to do in a class file. 

A typical model file will contain code such as, but not limited to the following:

* Custom scopes
* Model instance methods
* Default settings for database columns
* Validations
* Model-to-model relationships
* Callbacks
* Custom algorithms

### Creating an Active Record Model

Most developers are expected to build applications utilizing a Behavior Driven Development (BDD) processs, building each feature with a test-first approach. Begin with creating an RSpec rest. 

Using the example provided from Flatiron School, the below code and install the Rails gem sets up a basic skeleton of a Rails app;

```
# -T flag informs Rails generator not to include the default testing framework (TestUnit)
rails new rails-activerecord-models-and-rails-readme -T

# The Rails project generator creates the following directory:
cd rails-activerecord-models-and-rails-readme

bundle install

# Create initial RSpec config:
rails g rspec:install
```

After this initial setup, we'll create a new file for our `Post` model tests (`spec/models/post_spec.rb`) and write code that tests for 1) a `Post` is being created and 2) a new feature that returns a summary of a post. 

```
require 'rails_helper'

describe Post do

  # tests for a creation of a post
  it 'can be created' do
	  post = Post.create! (title: "My title", description: "The post description")
		expect(post).to be_valid
	end
	
	# tests for 'post_summary' feature
	it 'has a summary' do
	  post = Post.create!(title: "My title", description: "The post description")
		expect(post.post_summary).to eq("My title - The post description")
	end
end
```

Running the tests at this point will kick up an error without code in the `Post` model, as well as a *schema file*. We'll first update the model in the `app/models` directory (`app/models/post.rb`);

```
class Post < ActiveRecord::Base
end
```

*NOTE: Don't forget to inherit from `ActiveRecord::Base`, which gives you access to built-in methods we'll be testing for later!*

Running `rake db:migrate` will create the schema file. (We don't need to run `rake db:create`, because the test suite creates a test database for us to run our tests on.)

While we're able to actually start running our tests, using `bundle exec rspec`, we'll still encounter an error: `undefined method 'create!' for Post:Class`. We have a model, but didn't set up a database table for model to store data. To correct this, we'll create a new directory in the `db/` directory called `migrate`, and add a new file `001_create_posts.rb`;

```
class CreatePosts < ActiveRecord::Migration
  def change
	  create_table :posts do |t|
		  t.string :title
			t.text :description
			
			t.timestamps null: false
		end
	end
end
```

This basic migration creates a `posts` table with a title and description columns, along with built in timestamps. Run `rake db:migrate` to migrate your talble and update your `db/schema.rb` file. With all of this set in place, we'll have our first test passing, because `create!` is one of the many built-in methods of `ActiveRecord::Base`. Great! Now, onto the second test of the `post_summary` feature, which will fail without the `post_summary` method written for the `Post` model;

```
class Post < ActiveRecord::Base
  def post_summary
    self.title + " - " + self.description
  end
end
```

Now all your tests should be passing and, interestingly enough, without a controller, route, view, etc. This is because the application's data aspect is able to work seperately from the view and data flow logic. This separation of functionality makes it much easier to test data behavior on its own, because its not *strongly* coupled to how it's rendered to the user. When you do create controller and viewer files, however, make sure to follow proper naming conventions to ensure MVC assocations are readable. 

For example a controller for the provide 

due to theBecause the data aspect can work separately from the view and data flow logic, a controller was unnecessary for this demonstration. However, it is best to follow proper converntions when naming your controller and viewer files in order for MVC assocations to be readable. In this case, the controller for our `Post` model would be named `posts_controller.rb`, while our relevant view files are placed in a `views/posts/` directory. 

Unlike other programming languages, Rails automatically connects us to the database via the `config/database.yml` file, which is generated when `rake db:create` is run. The development, test, and production databases are all configured in this file. The `ActiveRecord::Base.connection` method then connects your application to the database; another benefit of model classes inheriting from the `ActiveRecord::Base` module.  

Rails provides developers with the ability to work in different environments, the `database.yml` file taking full advantage of this feature with its inclusion of different database options for each type of environemnt. Looking at the `databse.yml` fie, there are different database adapters, pools, timeout values, etc. Taiors for each environment specifically, it allows for setups such as using SQLite locallly and Postgres in production, as well as a segemented database environment for your testing suite. 

There are many components of the `database.yml` file only necessary for more advanced applications, but keep in mind that database configuration is kept here.


### **Keywords;**

* ***Active Record*** is the built-in ORM framework of Rails that manages database-related tasks. 
* ***ORM** (Object-Relational-Mapping)* is a programming technique for converting data between incomatible type systemsing using object-oriented programming languages. 
* ***SQL** (Structured Query Language* is a domain-specific languaged designed for managing data stored in databases.
* ***BDD** (Behavior Driven Development)* is a software development methodology that aims to simplify development through adapting natural language sentences and phrases into executable tests. 
* A ***schema file*** , which is automatically generated with database migrations, attempts to capture the current state of your databse schema.
