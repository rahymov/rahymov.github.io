---
layout: post
title:      "Recipe JavaScript Project"
date:       2019-03-28 02:42:38 +0000
permalink:  recipe_javascript_project
---

I have had done with my rails project long time ago but gave 1 month break to learning. With my JavaScript project learnt a lot. How to hijack then get the all recipes or whatever you want to. With ajax no need wait the http request response.AJAX is stand for Asynchronous JavaScript and XML. Instead XML nowdays using JSON(JavaScript Object Notation) wich makes human readable objects with attribute value. Ajax used with JQuery JavaScript library and open source software. JQuery is used easily write a client-side JS to manipulate and navigate the asynchronous Ajax callbacks. Understood how AJAX works. Here is what happening
1. In the background request made by ajax engine to the server and retrieve the data from the server.
2. HTML, XML, JavaScript format  data is returned to the browser by ajax engine.

In our project we used `active_model_serializers'` gem to serialize a model. After bundling we need to generate serializer to serialize models which we want. `rails g serialize recipe` and add attributes, associations to the comment serializer. 
``` 
class RecipeSerializer < ActiveModel::Serializer
     include Rails.application.routes.url_helpers

      attributes :id, :title, :description, :image
      belongs_to :user
      has_many :ingredients
      has_many :directions
      has_many :comments
      has_many :categories
      def image
        rails_blob_path(object.image, only_path: true) if object.image.attached?
      end
end
```
###### And added the code below recipes controller index: 
	
	```
	respond_to do |f|
      f.html { render :index}
      f.json { render json: @recipes}
    end
	```
	
###### And added the code below recipes controller show: 

```
   respond_to do |f|
      f.html { render :show}
      f.json {render json: @recipe}
    end
	```

Then when I done with controller next step was working on recipe.js. First thing to show index page when click the recipe navigation. Hijack the button when you click and show all recipes. Our goal is make ajax asynchronous request  meaning multiple events requesting independently of one another. 
``` 
   $(() => {
     listenForAllRecipesClick()
   });
```
The code  `$() ` shorthand  for `$( document ).ready()` , meaning method will run once the page DOM is ready to execute `JavaScript(JQuery)`  code.  Next step will execute function. Here is the code: 
 ```
 const listenForAllRecipesClick = () => {
  $('#all-recipes').on('click', e => {
    e.preventDefault();
    history.pushState(null, null, "recipes");
    getAllRecipes();
  })
  $(document).on('click', ".show-recipe", function(e){
    e.preventDefault()

    let id = $(this).attr('data-id')
    fetch(`/recipes/${id}.json`)
     .then(response => response.json())
       .then(recipe => {
         $('.app-container').html('')
         let newRecipe = new Recipe(recipe)
         let showRecipeHTML = newRecipe.recipeShowHTML()
         $(".app-container").append(showRecipeHTML)
     })
  })
}


const getAllRecipes = () => {
  fetch(`/recipes.json`)
    .then(response => response.json())
      .then(recipes => {
        $('.app-container').html('')
        recipes.forEach((recipe) => {
          let newRecipe = new Recipe(recipe)
          let allRecipesHTML = newRecipe.recipeIndexHTML()
          // debugger
          $(".app-container").append(allRecipesHTML);
          // console.log(newRecipe);
    })
  })
}


class Recipe {
  constructor(obj){
    this.id = obj.id
    this.title = obj.title
    this.description = obj.description
    this.image = obj.image
    this.user_email = obj.user.email
    // debugger
    // this.user.email = obj.user.email
    this.categories = obj.categories
    this.ingredients = obj.ingredients
    this.directions = obj.directions
    this.comments = obj.comments
  }
}


Recipe.prototype.recipeIndexHTML = function(){

  return(
    `
      <div class="row" id="recipes-list">
        <div class="col-md-4">
          <div class="recipe">
            <div class="image_wrapper">
              <a class="show-recipe" href="/recipes/${this.id}" data-id="${this.id}"><img src="${this.image}"></a>
            </div>
            <h4><a class="show-recipe" data-id="${this.id}" href="/recipes/${this.id}">${this.title}</a></h4>
          </div>
        </div>
      </div>
    `
  )
}
```

The code above when id with `#all-recipes` clicked `preventDefault()` refer to do not make action normally do. Instead get all recipes function. Fetch recipes.json which we searialized and can read in json format. Then response should be json format. Beforehand we have a recipe constructor with a object argument and assigning the object attributes to the this.attr. I have used Object prototyping which was requirement for JS project. JavaScript prototype is mechanism that objects inherit from one another. BasicallyJS prototype is inherit properties and methods form one another. That is meaning properties are available for other objects.I have created an Recipe object and call on them the indexHTML prototype on them(for every recipe object and associations). Thank you for reading :)
