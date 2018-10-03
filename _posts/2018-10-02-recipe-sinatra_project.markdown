---
layout: post
title:      "Recipe-Sinatra Project"
date:       2018-10-03 01:37:21 +0000
permalink:  recipe-sinatra_project
---

Hello everyone. I have created Recipe sinatra project that consist of user, category, recipe, recipe_categories models. Users could create new account and login. If user logged in could create recipe and see all recipes. If User created recipe could edit and delelete belonging recipe otherwise redirect to the recipes page. I have used ``` has_many through ``` associations recipe, category, recipe_categories

*********


File Structure: 

```
├── app
│   ├── controllers
│   │   ├── application_controller.rb
│   │   ├── categories_controller.rb
│   │   ├── recipes_controller.rb
│   │   └── users_controller.rb
│   ├── models
│   │   ├── category.rb
│   │   ├── recip_category.rb
│   │   ├── recipe.rb
│   │   ├── user.rb
│   │   
│   └── views
│       ├── categories
│       │   ├── category.erb
│       │   
│       ├── recipes
│       │   ├── edit.erb
│       │   ├── index.erb
│       │   ├── new.erb
│       │   └── results.erb
│       │   └── show.erb
│       ├
│       ├── users
│       ├    ├── create_user.erb
│       ├    ├── login.erb
│       ├    ├── show.erb
│       |    
│       ├── footer.erb
│       ├── header.erb
│       ├── home.erb
│       ├── layout.erb
├── config
|      ├── environment.rb
├── db
│     ├── migrate
│           ├── 20180925163632_create_users.rb
│           ├── 20180927171039_create_recipes.rb
│           ├── 20180929030513_create_categories.rb
│           ├── 20180929031801_create_recipe_categories.rb
│           ├── 20180929034257_add_missing_timestamps.rb
│
│── public
│             ├── application.css
│── config.ru
│── Gemfile    
│── Gelfile.lock
│── LICENSE.txt
│── Rakefile
│── Rakefile
│── README.md 

```

## Uploading Image to Sinatra Project

To upload image did research a lot not decided what gem could use. Most image upload gems are for rails app based. Found good article upload image without gems. And it's working well. Here is my some part of code: 

```
   class RecipesController < ApplicationController
	       post '/recipes' do
    if params[:title].blank? && params[:description].blank? && params[:ingredient].blank? && params[:directions].blank?
      redirect to 'recipes/new'

    else
      user = User.find_by_id(session[:user_id])
      # @categories = Category.find_by(params[:category_ids])
      @recipe = Recipe.new(title: params[:title],
                              description: params[:description],
                              ingredient: params[:ingredient],
                              directions: params[:ingredient],

                              image: params[:image],
                              :user_id => user.id)
      @recipe.category_ids = params[:categories]

      @filename = params[:file][:filename]
      file = params[:file][:tempfile]
      @recipe.image = @filename
      @recipe.save
      File.open("./public/#{@recipe.image}", 'wb') do |f|
        f.write(file.read)
      end
      flash[:message] = "Recipe created successfully."
      redirect to "/recipes/#{@recipe.id}"
    end
  end
end
```

* Creating ```@filename = params[:file][:filename]```
* Getting file ```file= params[:file][:tempfile] ```
* Update ```@recipe.image = @filename ```
* Open and write a file :
```File.open("./public/#{@recipe.image}", 'wb') do |f|
        f.write(file.read)
      end ```
			
	Here view actions: 
	```
    <div class="card-deck">
    <% @recipes.each do |recipe| %>
    <div class="card" style="width: 18rem;">
      <img class="card-img-top" src="<%= recipe.image %>" alt="<%= recipe.title %>">

      <div class="card-body">
        <h5 class="card-title" title="<%= recipe.title %>"><a href="/recipes/<%= recipe.id %>"><%= recipe.title %></a></h5>
        <p class="card-text"><%= recipe.description %></p>
      </div>
      <div class="card-footer">
        <small class="text-muted">by <%= recipe.user.username %></small>
      </div>
    </div>
    <% end %>
```

Thanks for visiting blog:)
