# Casting API Backend

## URL
----------


## Getting Started

The Casting Agency models a company that is responsible for creating movies and managing and assigning actors to those movies. You are an Executive Producer within the company and are creating a system to simplify and streamline your process.

### Installing Dependencies

#### Python 3.7

Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

#### Virtual Enviornment

We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organaized. Instructions for setting up a virual enviornment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)

#### PIP Dependencies

Once you have your virtual environment setup and running, install dependencies by naviging to the `/backend` directory and running:

```bash
pip install -r requirements.txt
```

This will install all of the required packages we selected within the `requirements.txt` file.

##### Key Dependencies

- [Flask](http://flask.pocoo.org/)  is a lightweight backend microservices framework. Flask is required to handle requests and responses.

- [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use handle the lightweight sqlite database. You'll primarily work in app.py and can reference models.py. 

- [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross origin requests from our frontend server. 

## Database Setup
Two DB in the folder
Development: Database.db
Test: Database_Test.db 

## Roles

- Casting Assistant
    Can view actors and movies
    
- Casting Director
    All permissions a Casting Assistant has and…
    Add or delete an actor from the database
    Modify actors or movies

- Executive Producer
    All permissions a Casting Director has and…
    Add or delete a movie from the database

### Permissions 
- Casting Assistant
    get:actors
    get:movies	

- Casting Director
    get:actors
    get:movies
    patch:actors
    patch:movies
    post:actors
    delete:actors

- Executive Producer
    get:actors
    get:movies
    patch:actors
    patch:movies
    post:actors
    post:movies
    delete:actors
    delete:movies

## Endpoints

GET '/movies'
GET '/actors'
DELETE '/movies/<int:id>'
DELETE '/actors/<int:id>'
POST '/movies'
POST '/actors'
PATCH '/movies/<int:id>'
PATCH '/actors/<int:id>'


GET '/movies'
- Fetches a list of movies
- Request Arguments: None
- Returns:  a list of movies
Example:
Response:
[
    {
        "title": "Scary Movie",
        "release date": 2002
    },
    {
        "title": "The Conjuring",
        "release date": 2002
    }
]


GET '/actors'
- Fetches a list of actors
- Request Arguments: None
- Returns:  a list of actors 
Example:
Response:
[
    {
        "name": "Abdullah Alhomaidhi",
        "age": 23,
        "gender": "male"
    },
    {
        "name": "Abdullah",
        "age": 23,
        "gender": "male"
    }
]

DELETE '/movies/<int:id>'
- Deletes a movie
- Request Arguments: id of a movie
- Returns: a success boolean and the id of the deleted movie
Example:
Request:  http://127.0.0.1:5000/movies/53
Response:
{
    "deleted": 53,
    "success": "True"
}

DELETE '/actors/<int:id>'
- Deletes an actor
- Request Arguments: id of an actor
- Returns: a success boolean and the id of the deleted actor
Example:
Request:  http://127.0.0.1:5000/actors/1
Response:
{
    "deleted": 1,
    "success": "True"
}

POST '/movies'
- Adds a movie
- Request Arguments: movie object with title and release date
- Returns: a success boolean and the id of the created movie
Example:
Request:  
{
    "title":"Scary Movie",
    "release_date": "2002"
}
Response:
{
    "created": 53,
    "success": "true"
}

POST '/actors'
- Adds a actor
- Request Arguments: actor object with name, age, and gender
- Returns: a success boolean and the id of the created actor
Example:
Request:  
{
    "name":"Abdullah",
    "age": "23",
    "gender": "male"
}
Response:
{
    "created": 4,
    "success": "true"
}

PATCH '/movies/<int:id>'
- Adds a movie
- Request Arguments: title or release date
- Returns: a success boolean and the id of the updated movie
Example:
Request:  http://127.0.0.1:5000/movies/53
{
    "release_date": "2002"
}
Response:
{
    "success": "true",
    "updated": 53
}

PATCH '/actors/<int:id>'
- Adds an actor
- Request Arguments: name, age or gender
- Returns: a success boolean and the id of the updated actor
Example:
Request:  http://127.0.0.1:5000/actors/3
{
    "name": "Abdullah Alhomaidhi"
}
Response:
{
    "success": "true",
    "updated": 3
}


### Errors

401
"success": False, 
"error": 401,
"message": "Unauthorized"

404
"success": False, 
"error": 404,
"message": "Not found"

422
"success": False, 
"error": 422,
"message": "Unprocessable Entity"

500
"success": False, 
"error": 500,
"message": "Internal Server Error"

## Testing
To run the tests, run

python test_app.py

## Setting up authentication

### login link

https://dev-tps54maa.us.auth0.com/authorize?
  response_type=token&
  client_id=dvxo5t6N9MttN7wPL3878BDDiszs3cB6&
  redirect_uri=https://localhost/5000&
scope=openid%20profile%20email&
audience=http://localhost:8080

### logout link

https://dev-tps54maa.us.auth0.com/v2/logout?
  client_id=dvxo5t6N9MttN7wPL3878BDDiszs3cB6&
  returnTo=http://localhost/5000

### credentials 

- Casting Assistant
   Username: CA@CA.com
   Passwrod: 123456aA

- Casting Director
   Username: CD@CD.com
   Passwrod: 123456aA

- Executive Producer
   Username: EP@EP.com
   Passwrod: 123456aA