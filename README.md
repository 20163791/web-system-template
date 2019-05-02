# Recipie getter
## Description
Recipie getter allows users to search for recipies by a main ingrediant.
The service gets a recipie and every time the user clicks next it fetches a new one. If the user hits "precious", it fetches the previous recipie.
The service shows yield and calories and igrediants. 
The service requires that a user signs up and logs in to use the service. The user can delete their account and change their password

## Entity definition
Recipie:
- uri	string (4000)	Ontology identifier
- label	string (1000)	Recipe title
- image	string	(4000) Image URL
- url	string (4000)	Original recipe URL
- yield	integer(1 to 999)	Number of servings
- calories	integer (1 to 99999) Total energy, kcal
- ingredients	Ingredient[]	Ingredients list

## API definition
GetRecipie(int ID) - gets recipie by its id  
GET https://api.edamam.com/search?r=[ID]&app_id=123&app_key=123  
returns 414 if too many arguments provided (GET string too long)  
returns 404 ID not found


GetRecipie(int calories | int ingredient number | int diet type string | int tim ) returns top 10 recipes by attribute(s)  
GET https://api.edamam.com/search?q=top_ingrediant&app_id=123&app_key=123&from=0&to=10&calories=min-max&ingr=numIngrediants&dishType=dishType$time=min-max  
returns 414 if too many arguments provided (GET string too long)  
error 404 ID not found


register(email, pass) adds a user to the database
PUT api/register
return 505 if email already in database
return 500 if other error


login(email, pass) logs a user in (provides a token)
POST api/login
retunr 500 if error


changePass(email, pass, newpass, newpass2) updates user password in db
POST api/change/pass
 reutrn 401 if incorect current pass
 return 400 if new passwords don't match
 return 500 if other errors


DeleteAccount(emai, token, pass) removes an account from db
DELETE api/:delete/account  
returns 401 if pass doesnt match session passs
return 500 if other


## UI definition
https://wireframe.cc/lUPkR2
