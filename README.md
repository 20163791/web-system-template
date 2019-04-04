# Recipie getter
## Description
Recipie getter allows users to search for recipies by a main ingrediant (ingrediants?), yield, calorie range and/or diet preferances 
The service gets the top 10 recipies that match the search and then allowes the suer to remove recipies from the lest, at wich point the next matching recipie is added.
The service shows yield and calories, and allowes the user to see how certain values would change if the yield was bigger/smaller or they wanted more/fewer calories in the recipie.

## Entity definition
Recipie:
- ID    Number (1 to 999999999) Entity identifier
- uri	string (4000)	Ontology identifier
- label	string (1000)	Recipe title
- image	string	(4000) Image URL
- source	string (4000)	Source site identifier
- url	string (4000)	Original recipe URL
- yield	integer(1 to 999)	Number of servings
- calories	integer (1 to 99999) Total energy, kcal
- ingredients	Ingredient[]	Ingredients list
- dietLabels	enum[]	Diet labels: “balanced”, “high-protein”, “high-fiber”, “low-fat”, “low-carb”, “low-sodium” (labels are per serving)
- healthLabels	enum[]	Health labels: “vegan”, “vegetarian”, “paleo”, “dairy-free”, “gluten-free”, “wheat-free”, “fat-free”, “low-sugar”, “egg-free”, “peanut-free”, “tree-nut-free”, “soy-free”, “fish-free”, “shellfish-free” (labels are per serving)


## API definition
GetRecipie(int ID) - gets recipie by its id  
GET https://api.edamam.com/search?r=[ID]&app_id=123&app_key=123  
returns 414 if too many arguments provided (GET string too long)  

GetRecipie(int calories | int ingredient number | int diet type string | int tim ) returns top 10 recipes by attribute(s)  
GET https://api.edamam.com/search?q=top_ingrediant&app_id=123&app_key=123&from=0&to=10&calories=min-max&ingr=numIngrediants&dishType=dishType$time=min-max  
returns 414 if too many arguments provided (GET string too long)  

DeleteRecipie(int ID) removes a recipie by id  
DELETE api/userID/recipieID  
returns 401 if userID does't match seasion userID  
returns 404 if resource doesn't exsist  

UpdateRecipie(int ID, int calories | int yield) updates recipie by ID and attribute   
POST api/userID/recipieID/atribute=newValue  
returns 401 if userID does't match seasion userID  
returns 404 if resource doesn't exsist  

## UI definition
https://wireframe.cc/lUPkR2
