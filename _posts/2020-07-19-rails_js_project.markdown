---
layout: post
title:      "Rails JS Project"
date:       2020-07-19 17:28:23 +0000
permalink:  rails_js_project
---


This week was focused on my JavaScript Project where I combined a Rails backend API with a JavaScript frontend. I found this project to be really interesting because it connected everything together that we've learned from the beginning. I'm very new to JavaScript and many of the underlying concepts, but I still enjoyed getting to see how you can manipulate the DOM to do pretty much whatever you can think of. 

Given my previous experiences with projects at Flatiron School, I decided to focus more on simplicity of the concept rather than try to build real world applications. However, I also wanted the project to be something I could use in the future, so I set to create a repository of past vacations I enjoyed to share recommendations with friends and family.

To start out, I decided to create a backend that contained a single has-many relationship model structure. I used State and City models as the overrall concept for a U.S. based vacation journal application. For the serializer, I opted for the Fast JSON Netlfix created option. I thought it was pretty cool that Netflix also makes tools like this. I had no idea they made these types of tools available to anyone. I found this way to be a little difficult only because the result was in this nested JSON that was a bit more difficult to grab keys from than in the examples I learned about. Active Model Serializer in retrospect may have been a little more clear. Although getting started with Fast JSON was pretty simple to start up. 

To start just add gem 'fast_jsonapi' to your gemfile. 

After this, run bundle install in your terminal (make sure you cd into your rails-backend directory first)

Once installed, Fast JSON allows you to use rails built in generator capability to create serializers for your models. 
So if you ran: 

```
rails g serializer Widget

```

This would create a directory inside your app called app/serializers/widget_serializer.rb. What was nice about this was you could then actually specify the attributes you wanted to include in the data serialization process as well as the active record relationships you would normally just define inside your models (has-many, belongs_to, etc). 

Inside of your Widgets Controller, when defining actions like index and show, instead of just simply calling (in standard rails): 

```
@widget = Widget.find_by(id: params[:id])
render json: @widget

```

or 

```
@widgets = Widget.all
render json: @widgets
```

You could instead change render json to: 

```
render json: WidgetSerializer.new(widget)
or
render json: WidgetSerializer.new(widgets)
```

which initalizes serialization of a widget or an array of these widgets. This process allows you to access the same routes you normally would (index, show) but instead of rendering an HTML page, you are able to see JSON hash-like object and the specified attributes like :name, :id, etc and even associated models. 

For the frontend of this project I decided to try to create modular JS and break up classes. This proved to be a complex process and probably overkill for the purposes of this project. I wanted to create class adapters that served to provide fetch calls to the backend and then allow the classes to access their methods. This works but a more simple approach of two class files (example.js and example2.js) would have been better. After discussing with my instructor I would have probably done this instead. 

One of the first things I wanted to do with this app was be able to select a state from a dropdown list. In regular rails, this was a simple process (fairly simple) where you could call collection_select inside your formhelper (form_for and form_with) and accessing something like Widget.all and associated models. I had this in Sinatra as well with regular html <option> and <select> tags. 

In JS, getting a dropdown box populated with backend JSON is a bit tricker. In my case, not only did I want to display a list of items, I wanted to add this dropdown box inside of the submittable form on the DOM. Basically I had to call a fetch request to the states index page (where I had nested JSON) and then dig into the proper layer of the hash to find the appropriate key with which to extract name data. In the lessons I had completed, simply accessing the data response object ( in the second .then) would allow me to call a .forEach method I could than use to iterate through and capture the :names. It took me a little while to see that I had to step into this hash and actually see that data was inside another data "hash-like" - I could then get access to the attributes  inside (name and code). So then, I created a 'select' tag by calling document.createElement and setting it equal to stateSelect. Because I had defined a variable called states that was equal to data.data I could now use for(let state of states) and be able to iterate through this array. Inside of states, I used createElement again to create an option tag by setting a variable called option. Once option was defined I could then set a .value method equal to the state id (one level up from the attributes hash). I could also set the text of the option variable equal to the state.attributes.name. I had some help from my classmate on this - it was very helpful and generous. Still inside of this for block, I appended option to the select tag I created with the stateSelect variable. Finally I appended this stateSelect which contained all the option data to the filter-drop-down container. This was definitely the most proud I was with my project. I was able to use JS frontend to call the backend. Also, I seeded  the backend with all fifty states by iterating through an array of states and creating them in a single .each block. 

Overrall I really liked the experience of working on this project. I think if I simplified the frontend structure I could have saved some time. Its really amazing to think how far I've come since I started at this school. 


