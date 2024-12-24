---
title: "Rails Views with multiple assocations"
date: 2024-12-24T08:21:26-05:00
draft: true
featuredImage: 
featuredImageAlt:
---
I am learning how to create and handle Rails ActionViews with multiple associations. There are many ways to handle associations in rails and I have not seen a consistent use of one paradigm. It is a challenge to think through which should come first or what associated data may already be in the database, and there is no need to recreate a create form view for this component. 

The key component is learning which model will load the most tables when performing the save action ```@model.save``` when handling multiple tables because of associated models.

## Many-to-Many Example
For example, if you save the join table[^1] model, then the model's save action will commit in one database transaction 3 inserts when save is performed:

1. Insert into a table that a has_many reference to the join table.
2. Insert into a table that has the second has_many reference to the join table.
3. Finally, the join table will insert the "connection or join" references.

Contrast this to saving each model separately, it is a lot of work (many instance variables), but it also introduces potential database inconsistencies.

By saving and committing 3 transactions in one transaction, you will avoid any database errors if you were to manually perform a ```@model.save``` on three separate variables independently. There could be a potential database inconsistency should one of the inserts fails to save.

## Params Hashs

At the end of the day, params is a hash.[^2] The params can include any values you set in the view. You must expect, require and permit them of course. You just have to use create a symbol in the view and expect it in the controller and you can create as many model objects as required.

For example, here's how to set a symbol as a :tag.

```<%= form.text_field :tag %>```

Then you can expect your field via params.expect(model: [:tag]) in your controller and set it to your model object in your controller and save to your data base.

#### Sources and Credits:
[^1]: https://guides.rubyonrails.org/association_basics.html#has-many-through
[^2]: https://guides.rubyonrails.org/form_helpers.html#form-input-naming-conventions-and-params-hash
