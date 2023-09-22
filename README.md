# Receipe Web API

The goal of this project is to build a web API where users can sign up and post different dishes, their receipe and the process of making it.
## Routes

The API have these endpoints.

#### No Auth Routes

* `GET /receipe` get all receipes  ` projection  {title, _id, indegeniousToWhatTribe, ingredients}`
*  `GET /receipe/:id` get all the information of a particular receipe
*  `GET /user/:id` return all receipes of the user with the id  `{title,_id,indegeniousToWhatTribe, ingredients} and username and email`
*  `POST /auth/signup` => create a user  `submitting {username, password, name, email[unique] } : all required`
*  `POST /auth/login` => Log a user in  `{username , password} : all required`

#### Auth Route

* `POST /createNewRecipe`
* `GET /mymeals` all receipes of this user
* `Delete /receipe/id` [req would only proceed if its from the user]
* `PUT /receipe/id` Edit the receipe with this ID [should not be able to edit title]

* `GET /users/profile` returns the logged in users details without his receipes but a field bearing NumberofMeals = the number of receipes he own
* `PUT /users/profile` Edit the logged in user profile [except the password & role & createdOn]
* `PUT /users/settings ` Change the user password and invalidate every other logged in users token


### Schema should look something like this

```
    userschema {
        name[required],
        email[required & unique],
        password[requierd],
        receipes 
    }

    steps : {
        step : Number,
        detail : String
    }
    receipeSchema{
        title,
        ingredients [Array of strings],
        process [Array of steps],
        createdBy,
        postedOn
    }
```


