---
layout: post
title:      "form tag helper for search "
date:       2020-06-22 11:58:10 -0400
permalink:  form_tag_helper_for_search
---


The form_tag helper is used as a way to assign values to a form manually instead of like using form_for which takes in an object or instance of your model. I used form_tag to create a search query inside my Clients index page. The form_tag helper in my case works as follows: 

<%= form_tag '/search', method: :get do %>
   <%= label_tag "Look Up Client Name" %>
   <%= text_field_tag :search %>
   <%= submit_tag "search", :name => nil %>
<%end%>

The first line of the code is evaluating the form_tag helper method. First the '/search' action is being called which is routed to the clients#index route. In order to make this work, you need to call the 'get' method on this route.  After this, a 'do' is added to establish a block where the rest of the form_tag code will be written. 

The next line of code is the label_tag - this just establishes the name for the field you are creating. In my case this is called "Look Up Client Name" but could really called anything. 

The following line of code, text_field_tag is where I'm adding a field name :search and :search id  (if inspecting the page you can see these attributes) - which is coming from params[:search] - this is permitted or whitelisted through client params in the clients controller. That information is coming from the class method created inside of the Client Model. - self.search(search) - the argument here is then applied within the method itself. The text_field_tag line is the line that accepts in the value I type into the input box through params (that value can been inside of the inspection of the page ie. "Am" for Amazing). 

I have edited the text_field_tag line of code to reflect that only :search  is being used instead of <%=text_field_tag:search, params[:search] %>. The new code should read: 
<%=text_field_tag :search %> as highlighted above inside the block. After further review, including params[:search] as second argument wasn't necessary to fulfill the search function. 

The last line of this form is an actual submit button or submit_tag  which sends the form data I type in. The first part of this defines the title of submit button, in this case, "search". The second of this line of code isn't really necessary after I reviewed this further, you can still use this search form but inside of the url bar you get a &commit=search. I'm not 100% sure but I think a  regular submit should be able to handle this submission. 

At the end, there is an end statement which closes the block and any code executed inside of it. 

This is my best understanding of this form at this point. I know the form_for and form_with helpers are generally more powerful because these allow you to work with objects. 
