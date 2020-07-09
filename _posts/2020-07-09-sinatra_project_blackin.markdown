---
layout: post
title:      "Sinatra Project (BlackIn)"
date:       2020-07-09 13:50:11 -0400
permalink:  sinatra_project_blackin
---


It was a journey getting through this project. This project was inspired by my sister who is insistent on buying things only from black owned businesses. I was online one day helping her find nail polishes by black own businesses and it took almost an HOUR! We found a website that was supposed to show us all black own businesses, but it's functionality wasn't the greatest. 

I started this journey with researching what businesses in Atlanta were black owned. I was able to retrieve an excel sheet and saved it as csv file. (Shoutout to this blogpost: [Seed your DB in 15 Mins or Less](https://medium.com/@gene.y.yoo/seed-your-db-in-15-mins-or-less-fake-data-33c18b10d110/) 
I used this code:
```
require 'csv'
CSV.foreach('csv_folder/Eateries.csv') do |row|
  name = row[1]
  owner = row[2]
  type_of_food = row[3]
  neighborhood = row[4]
  address = row[5]
  website = row[6]
  instagram = row[7]
  Eatery.create(name: name, owner: owner, type_of_food: type_of_food, neighborhood: neighborhood, address: address, website: website, instagram: instagram) 
end
```

From there it allowed me to take that information and create a simple experience. Users are able to create a profile.

```
<h1>User Sign Up</h1>
<br/>
<br/>
<%= @error %>
<form method="POST" action="/user">
<label>First Name:</label>
<input type="text" name="user[first_name]"/><br/>
<label>Last Name:</label>
<input type="text" name="user[last_name]"/><br/>
<label>Email:</label>
<input type="email" name="user[email]"/><br/>
<label>Password:</label>
<input type="password" name="user[password]" >
<br/>
<input type="submit" value="Sign Up"/>
</form>
```

View Eatery options and Rate them.

```
<a href="/user/<%= current_user.id %>"><input type="submit" value="Profile"></a><a href="/eatery"> <input type="submit" value="Eateries"></a> <a href="/logout"><input type="submit" value="Logout"/> </a>
<br/>
<br/>
<h1>Single Eatery</h1><br>
<br>
<h2>Name:         <%= @eatery.name %></h2>
<h2>Cuisine:      <%= @eatery.type_of_food %></h2>
<h2>Neighborhood: <%= @eatery.neighborhood %></h2>
<h2>Address:      <%= @eatery.address %></h2>
<h2>Website:      <a href="<%= @eatery.website %>"> <%= @eatery.website %> </a></h2> 
<h2>Instagram: @<%= @eatery.instagram %></h2><br>
<br>
<br/>
<br/>
<br/>
<h1>Rating this Eatery</h1>
<br>
<br>
<form method="POST" action="/rating">
<input type="hidden" name="rating[eatery_id]" id="rating[eatery_id]" value="<%= @eatery.id %>"/>
<input type="hidden" name="rating[eatery_name]" id="rating[eatery_name]" value="<%= @eatery.name %>"/>
<input type="hidden" name="rating[user_id]" id="rating[user_id]" value="<%= session[:user_id] %>"/>
<label>Customer Service:</label>
<input type="radio" name="rating[customer_service]" value="0"> bad
<input type="radio" name="rating[customer_service]" value="5"> okay
<input type="radio" name="rating[customer_service]" value="10" checked> good
<br/>
<label>Product Quality:</label>
<input type="radio" name="rating[product_quality]" value="0"> bad
<input type="radio" name="rating[product_quality]" value="5"> okay
<input type="radio" name="rating[product_quality]" value="10" checked> good
<br/>
<label>Checkout Experience:</label>
<input type="radio" name="rating[checkout_experience]" value="0"> bad
<input type="radio" name="rating[checkout_experience]" value="5"> okay
<input type="radio" name="rating[checkout_experience]" value="10" checked> good
<br/>
<label>Overall Experience:</label>
<input type="radio" name="rating[overall_experience]" value="0"> bad
<input type="radio" name="rating[overall_experience]" value="5"> okay
<input type="radio" name="rating[overall_experience]" value="10" checked> good
<br/>
<br/>
<input type="submit" value="submit"/>
</form>
```

This is definitely a project that I intend to build from. I hope that you enjoy the beginning of something big.

[Blackin App](https://github.com/emerykurt/BlackIn)
