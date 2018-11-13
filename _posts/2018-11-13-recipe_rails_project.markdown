---
layout: post
title:      "Recipe Rails project"
date:       2018-11-13 17:05:48 +0000
permalink:  recipe_rails_project
---

Hello everyone. I have extended my sinatra project on rails. I had some challenges but learn a lot of new things. First thing I think about project what features I can add. Draw the tables on the paper and online free [database design tool](https://www.dbdesigner.net/) to see tables connections and columns. I think first step to build a project should be models(database) design. To authenticate user used `devise gem`.  I have users, recipe, ingredient, direction, category, recipe_category, rate,  review, comment models.  Here is models:

user.rb: 
``` 
has_many :recipes
has_many :reviews, dependent: :destroy
has_many :comments
```

recipe.rb: 
```
belongs_to :user
has_many :recipe_categories
has_many :categories, through: :recipe_categories
has_many :directions
has_many :ingredients
has_many :reviews
has_many :comments, :dependent => :destroy
```

category.rb: 
```
has_many :recipe_categories
has_many :recipes, through: :recipe_categories
```
##### join table for recipe&category
recipe_category.rb: 
```
belongs_to :category
belongs_to :recipe
```

ingredient.rb: 
```
belongs_to :recipe
```

direction.rb: 
```
belongs_to :recipe
```

comment.rb: 
```
belongs_to :recipe
belongs_to :user
```

review.rb: 
```
belongs_to :user
belongs_to :recipe
```

Recipe could be created by any `current_user(if logged_in)` by recipe title, description, categories(check_box), add direction, ingredient, image. Upload image through rails active_storage. Before I used paperclip and carrirwave gems. All categories are created before in `seed.rb` file. Directions, ingredients are `nested forms` and used `cocoon gem` . Here is nested form attributes: 
```
accepts_nested_attributes_for :ingredients, reject_if: proc {|attributes| attributes['name'].blank?}, allow_destroy: true
accepts_nested_attributes_for :directions, reject_if: proc {|attributes| attributes['step'].blank?}, allow_destroy: true
```

When user get on app no need to login to see all recipes and show page but all other actions needed to be logged in. User could not edit or delete someone else recipes and disabled edit ,delete buttons.
Recipe application has search functionality used ransack gem because last project implemented basic search functionality and want to try new things.
I want share some usage of activestorage codes. ActiveStorage builnt-in gem in Rails 5.2 to handle  files upload to Amazon S3, Google Cloud Service, Microsoft Azure and attach that files to the ActiveRecord objects. Installation: 
`rails active_storage:install` will create tables then `rails db:migrate` to run migrations. If you want to use local store development environment config/environments/development.rb:
`config.active_storage.service = :local `
To use the test service when testing, you add the following to config/environments/test.rb: 
`config.active_storage.service = :test`
Then recipe.rb model has_attachment: 
```
class Recipe < ApplicationRecord
  has_one_attached :image
end
```
Here is controller and views: 
```
class RecipeController < ApplicationController

private 
  def recipe_params
      params.require(:recipe).permit(
          :title, :description, :user_id, :image,
          ingredients_attributes:[:id, :name, :_destroy],
  				directions_attributes: [:id, :step, :_destroy],
          category_ids: [] )
    end
```

`show.html.erb`: 
```
<% if @recipe.image.attached? %>
    <span><%= image_tag @recipe.image.variant(resize: '500x500'), class: "recipe_image", placeholder: "image" %></span>
  <% else %>
    <%= image_tag "logo.jpg" %>
  <% end %>
```
` index.html.erb`:
```
<%= image_tag recipe.image.variant(resize: '300x300') %>
```
And to use variant resize image add routes to routes.rb:
```
resolve("ActiveStorage::Variant") { |variant, options| main_app.route_for(:rails_variant, variant, options) }
```
If you need more info check out [active_storage](https://edgeguides.rubyonrails.org/active_storage_overview.html)
Thank you:)
