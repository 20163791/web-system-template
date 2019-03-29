# Recipie getter
## Description
Recipie getter allows users to search for recipies by a main ingrediant (ingrediants?), yield, calorie range and/or diet preferances 
The service gets the top 10 recipies that match the search and then allowes the suer to remove recipies from the lest, at wich point the next matching recipie is added.
The service shows yield and calories, and allowes the user to see how certain values would change if the yield was bigger/smaller or they wanted more/fewer calories in the recipie.

## Entity definition
Recipie:
- ID    Number  Entity identifier
- uri	string	Ontology identifier
- label	string	Recipe title
- image	string	Image URL
- source	string	Source site identifier
- url	string	Original recipe URL
- yield	integer	Number of servings
- calories	integer Total energy, kcal
- ingredients	Ingredient[]	Ingredients list
- dietLabels	enum[]	Diet labels: “balanced”, “high-protein”, “high-fiber”, “low-fat”, “low-carb”, “low-sodium” (labels are per serving)
- healthLabels	enum[]	Health labels: “vegan”, “vegetarian”, “paleo”, “dairy-free”, “gluten-free”, “wheat-free”, “fat-free”, “low-sugar”, “egg-free”, “peanut-free”, “tree-nut-free”, “soy-free”, “fish-free”, “shellfish-free” (labels are per serving)


## API definition
GetRecipie(int ID) - gets recipie by its id

GetRecipie(int calories | int yield | ingredients []) returns top 10 recipes by attribute(s) 

DeleteRecipie(int ID) removes a recipie by id

UpdateRecipie(int ID, int calories | int yield) updates recipie by ID and attribute 


## UI definition
https://wireframe.cc/lUPkR2
