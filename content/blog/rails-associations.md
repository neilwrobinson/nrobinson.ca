---
title: "Rails Associations"
date: 2024-12-21T13:36:31-05:00
draft: false
featuredImage: "/images/2024-12-21/database-schema.jpg"
featuredImageAlt: "Picture of a Database Schema"
tags: ["Rails", "Rails models", "Ruby on Rails"]

---
In Ruby on Rails, the MVC concept is easy to follow when you have a non-relational type of model. The difficulty with rails is that I find organizing and creating the MVC around multiple model associations. The resources and views of associated models seem linked together and brittle. As if I make a change and it breaks a lot of the default views code or the create and update actions. I fear I am misunderstanding rails. I looked through all the guides and there doesn't appear to be good explanation for how to deal with the views of complex associations. Even on the web, there seems to be limited discussion on this topic.

I understand the modeling portion in the Active Record Associations guide. But getting it all glued together in the views is definitely not as straight-forward.

The only good example I have found was in the Getting started Guide prior to rails 8. It's the classic Blog app. The example near the end of the guide adds a sub-resource, i.e. the sub-resource is the comments of a blog article. It is an ownership resource. (i.e. each article owns its own comments). This is a nested resource and rails seems to handle this quite great. However, if you have more complex modeling the ownership association may not be relevant or prevalent in your resources, and naturally the glue to get them to work together is a lot of work. I would also note that the Rails Routing Guide[^1] states "The general rule of thumb is to only nest resources 1 level deep." you cannot use nested resources all the time; you should use them judiciously. With this sub-resource limit, you cannot model your app on this view all the time.

The only way to solve this problem is start digging deeper for solutions.

Cover image credit[^2]

[^1]: Source: 
https://guides.rubyonrails.org/routing.html#limits-to-nesting

[^2]: Image Credit: 
"database schema" by gnizr is licensed under CC BY 2.0. To view a copy of this license, visit https://creativecommons.org/licenses/by/2.0/?ref=openverse.
