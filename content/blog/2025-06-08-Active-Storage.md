---
title: "Active Storage Awesomeness and Challenges"
date: 2025-06-08T16:28:33-04:00
draft: false
featuredImage: "/images/2024-12-24/2024-12-24-Rails-Views.webp"
featuredImageAlt: "Picture of a Rails ActionView field_for :tag example"
tags: ["Active Storage","Rails", "Rails models", "Ruby on Rails"]
---

Rails Active Storage is incredible piece of software. Its purpose is to manage object storage (or cloud storage buckets). Active Storage makes it straightforward to include file attachments via forms when using rails. I used the carrierwave gem before, and using a file storage built into Rails seems like a better idea than adding another external gem.

<!--more-->

I appreciate the polymorphic table design. You can have one storage table that can reference all your different Active Record models to a particular file. Checkout the Polymorphic Join Table picture on this blog post for a visual.[^1]

## Authenticated Controllers with Active Storage

The public buckets are public by default. The URL is publicly exposed once the URL becomes known. The URL would be difficult to guess. The URL is permanent, and if a person knows and goes directly to the URL it would by pass any protections in your Rails controller. You must be aware of what you are attaching using Active Storage to ensure you are not exposing information unintentionally.
To remove publicly accessible URLs, configure this:
```
config.active_storage.draw_routes = false
```
The configuration will disable Active Storage default routes.

Then you have to implement your own authorized / authenticated controllers to show the files or blobs you want to expose. 

## My Usage
I am trying to keep dependencies and extra cost at a minimum right now, and I am using active storage as a local object storage on the servers hard disk instead of on a public cloud buckets such as GCP, AWS, or MS Azure. It is another item to backup, but for now it should be okay since it is relatively a small bucket.

Sources
[^1]: Active Storage Blog, see polymorphic table. https://pragmaticstudio.com/tutorials/using-active-storage-in-rails

