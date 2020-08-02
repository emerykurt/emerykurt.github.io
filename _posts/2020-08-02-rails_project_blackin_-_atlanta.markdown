---
layout: post
title:      "Rails Project (BlackIn - Atlanta)"
date:       2020-08-02 15:54:56 -0400
permalink:  rails_project_blackin_-_atlanta
---


This project was a fulfilling experience. Rails is like the fairy god mother of ruby and my project is Cinderella. I was impressed with a couple of things from the rails g capabilities to routes and the dreadful Google Oauth. 

The command lines for rails is the magic of rails. If you start off with `rails --help` you given this output:

```
The most common rails commands are:
 generate     Generate new code (short-cut alias: "g")
 console      Start the Rails console (short-cut alias: "c")
 server       Start the Rails server (short-cut alias: "s")
 test         Run tests except system tests (short-cut alias: "t")
 test:system  Run system tests
 dbconsole    Start a console for the database specified in config/database.yml
              (short-cut alias: "db")

 new          Create a new Rails application. "rails new my_app" creates a
              new application called MyApp in "./my_app"


All commands can be run with -h (or --help) for more information.
.....
```

(There are some parts that I left out for later.)

Of course, just looking at the options it makes sense to start with `rails new application_name`. 

This gives you the foundation of your application with things such as your app folder (which includes MVC folders amongst other things,) routes file, database folder, GEM file, etc. Imagine if we had to go in and create each one of these by hand.

Next I generated models by using `rails g model_name model_attribute model_attribute model_attribute`. Not only did it generate the model, but the migration with the attributes (for specification: If you do not put a field type, then it will automatically choose a string for you. For example if you wanted to add the attribute of their age it would look like: `rails g model_name username first_name last_name age:integer password_digest `. I just ran a mock up and here were the migration results for `rails g model_name username first_name last_name password_digest `:

```
class CreateUsers < ActiveRecord::Migration[6.0]
  def change
    create_table :users do |t|
      t.string :username
      t.string :first_name
      t.string :last_name
      t.string :password_digest

      t.timestamps
    end
  end
end
```

Amazing right?!?! That is one third of your MVC! The next step woud be generating a controller. I wonder what the command would be for that? If you guessed `rails g controller` then you are already thinking in the right direction! The full syntax would be: `rails generate controller ControllerName :action :action` In my mock up I have put `rails generate controller  User :create :new :show :edit` Which resulted in:

```
create  app/controllers/user_controller.rb
       route  get 'user/:create'
get 'user/:new'
get 'user/:show'
get 'user/:edit'
      invoke  erb
      create    app/views/user
      create    app/views/user/:create.html.erb
      create    app/views/user/:new.html.erb
      create    app/views/user/:show.html.erb
      create    app/views/user/:edit.html.erb
      invoke  test_unit
      create    test/controllers/user_controller_test.rb
      invoke  helper
      create    app/helpers/user_helper.rb
      invoke    test_unit
      invoke  assets
      invoke    scss
      create      app/assets/stylesheets/user.scss
```

So not only did it create our `UserController` but we now have routes for create action, new action, show action, and edit action. Then on top of that they have provided us with:

```
     create    app/views/user
      create    app/views/user/:create.html.erb
      create    app/views/user/:new.html.erb
      create    app/views/user/:show.html.erb
      create    app/views/user/:edit.html.erb
```

The foundation for MVC and our rails app has now been created in a matter of minutes and now it is all about customizing to your needs. 

I hope you enjoy my project: [BlackIn ATL](https://github.com/emerykurt/blackinatlapp)

Happy Coding!
