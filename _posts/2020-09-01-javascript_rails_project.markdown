---
layout: post
title:      "JavaScript/Rails Project !"
date:       2020-09-01 00:18:02 -0400
permalink:  javascript_rails_project
---



The hurricane that is JavaScript. I began this project thinking about my next steps in life. Remember when [Facebook](http://www.facebook.com) was only for college students. Well, I felt like that was quite appropiate for a code bootcamp student who is about to graduate in a month. 

Talk about a tough cookie to swallow. Of course the first part was setting up my backend. I can't believe it was so easy! (About four months ago I didn't think I would be saying that. Utilizing things like `rails generate` that made the app up and running in about 20 min. (Can you believe there is a guy that has done it in 5?!?!)

There was an important factor when thinking about #JavaScript you have to setup your `cors.rb`. It's actually fairly simple:

``` Rails.application.config.middleware.insert_before 0, Rack::Cors do
    allow do
      origins '*'
  
      resource '*',
        headers: :any,
        methods: [:get, :post, :put, :patch, :delete]
    end
  end ``` 
	
	Another thing that is important is setting up your serializers and how you call them. The setup in my project looked a little like:
	
	```class CompanySerializer
  include FastJsonapi::ObjectSerializer
  attributes :id, :name, :hq_city, :hq_state, :mission_statement, :website, :twitter
  has_many :ratings
end```

```class RatingSerializer
  include FastJsonapi::ObjectSerializer
  attributes :id, :process, :lifestyle, :compensation, :mentorship, :diversity, :fname, :lname, :bootcamp, :city, :state, :company_id```
  
  ```attribute :company do |object|
    CompanySerializer.new(object.company)
  end
end```

Notice the slight, but magical difference........have you seen it yet. If you haven't let me specify what I am talking about.

```attribute :company do |object|
    CompanySerializer.new(object.company)
  end
end```

Ratings `belongs_to` Company so this line code interates through each rating and pulls out it's company association WITH its information. It's the small details that make a difference on a sight. 


A big focus for me was understanding constructors and static methods. (They are the reason why project works.) Constructor method is a unique method that creates and initialize an object created in the class. Classes are similar to classes in Ruby. In javascript function declarations are hoisted and class declarations are not. You have to call class functions for them to run. Static functions are called without instantiation and they also can't be called through a class instance. That is not even the toughest part. The challenge if you are not careful (of course I wasn't) is that if you want to pass an object you must call a method to find it. Which ultimately means you have to create that method as well. Here is an example:

```static handleReviewClicks = (e) => {
        // debugger
        if (e.target.className === "update"){
            let id = e.path[0].dataset.id
            Ratings.findById(id)
        }
    }``` 
		
```static findById = (e) => {
            // debugger
            fetch(`http://localhost:3000/ratings/${e}`)
            .then(res => res.json().then(json =>{
                let rating = new Ratings(json.data)
                rating.updateReview(json.data)
            }))
    }```
		
		```updateReview = (e) => { ${insert code here} } ```

As you can see an extra step was implemented, but it really expresses the magic of static methods.
		
		

Checkout my project [here](https://github.com/emerykurt/companyclick/tree/oo-version)!
