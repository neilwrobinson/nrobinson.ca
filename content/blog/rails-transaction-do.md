---
title: "Rails Transaction Do"
date: 2025-01-15T21:58:48-05:00
draft: true
featuredImage: "/images/2024-12-24/2024-12-24-Rails-Views.webp"
featuredImageAlt: "Picture of a Rails ActionView field_for :tag example"
tags: ["Rails", "Transactions", "Rails models", "Ruby on Rails"]
---

# ActiveRecord Transactions

You can commit atomic transactions on an ActiveRecord model by calling class method Model.transaction do. This allows the update controller action to update all associated models in one transaction. I have previously wondered how to make sure you can update all your associated models in one big committed transaction and ensure all models are updated through the controller. Now I learned it is using the transaction do block. 

```
Book.transaction do
  book.title(“Alice in Wonderland”)
  author.name(“Lewis Carroll”)
end
```

# #save and #destroy
The #save and #destroy methods automatically are wrapped in the transaction do call, so there is protection to ensure models ensure database integral referentiality. 

# Updating Records 
The transaction do block could be useful for the update resource in the CRUD actions in rails (create, read, update, and destroy).

Particularly because the update does not commit all models to be saved in one committed transaction.

You can call the #update on the model with supplied params. For instance:
```
class Book < ApplicationRecord
  def update(book_params, author_params)
    Book.transaction do
      book.update(book_params)
      author.update(author_params)
    end
  end
end
```
