#  API 
this api allows us to collect existing books and categories for various uses, to add new categories as well as new books, to modify or even supress certain books
## Getting Started

### Installing Dependencies

#### Python  3.10.1
#### pip 20.0.3 from /usr/lib/python3/dist-packages/pip (python  3.10.1)

Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

#### Virtual Enviornment

We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organaized. Instructions for setting up a virual enviornment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)

#### PIP Dependencies

Once you have your virtual environment setup and running, install dependencies by naviging to the `/livres(books)_api` directory and running:

```bash
pip install -r requirements.txt
or
pip3 install -r requirements.txt
```

This will install all of the required packages we selected within the `requirements.txt` file.

##### Key Dependencies

- [Flask](http://flask.pocoo.org/)  is a lightweight backend microservices framework. Flask is required to handle requests and responses.

- [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use handle the lightweight sqlite database. You'll primarily work in app.py and can reference models.py. 

- [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross origin requests from our frontend server. 

## Database Setup
With Postgres running, restore a database using the livres(books)_database.sql file provided. From the backend folder in terminal run:
```bash
psql projetflask_database < projetflask.sql
```

## Running the server

From within the `Library_api` directory first ensure you are working using your created virtual environment.

To run the server on Linux or Mac, execute:

```bash
export FLASK_APP=Nancy.py
export FLASK_ENV=development
flask run
```
To run the server on Windows, execute:

```bash
set FLASK_APP=Nancy.py
set FLASK_ENV=development
flask run
```

Setting the `FLASK_ENV` variable to `development` will detect file changes and restart the server automatically.

Setting the `FLASK_APP` variable to `flaskr` directs flask to use the `flaskr` directory and the `__init__.py` file to find the application. 

## API REFERENCE

Getting starter

Base URL: At present this app can only be run locally and is not hosted as a base URL. The backend app is hosted at the default, http://localhost:5000; which is set as a proxy in frontend configuration.

## Error Handling
Errors are retourned as JSON objects in the following format:
{
    "success":False
    "error": 400
    "message":"Bad request
}

The API will return four error types when requests fail:
. 400: Bad request
. 500: Internal server error
. 422: Unprocessable
. 404: Not found

## Endpoints
. ## GET/livres

    GENERAL:
        This endpoints returns a list of livres object, success value, total number of the livres. 
    
        
    SAMPLE: curl http://localhost:5000/livres

     {
    "Livres": [
        {
            "auteur": "Laurent Gaulet",
            "categorie_id": 1,
            "date_publication": "Wed, 10 Nov 2021 00:00:00 GMT",
            "editeur": " First ›",
            "id": 2,
            "isbn": "978-2-4120-7300-1",
            "titre": "Officiel de l'humour 2022 : + de 1 500 blagues 100 % fous rires"
        },
        {
            "auteur": " Michelle Marly",
            "categorie_id": 1,
            "date_publication": "Thu, 10 Feb 2022 00:00:00 GMT",
            "editeur": " Fleuve éditions ",
            "id": 3,
            "isbn": "978-2-2651-5546-6",
            "titre": "Romy et les lumières de Paris"
        },
        {
            "auteur": "Frédéric Quinonero",
            "categorie_id": 1,
            "date_publication": "Thu, 03 Feb 2022 00:00:00 GMT",
            "editeur": "Archipel ›",
            "id": 4,
            "isbn": " 978-2-8098-4175-6",
            "titre": "Julien Doré"
        },
        {
            "auteur": "Sempé",
            "categorie_id": 2,
            "date_publication": "Thu, 04 Nov 2021 00:00:00 GMT",
            "editeur": " Denoël ›",
            "id": 5,
            "isbn": "978-2-2071-6419-8",
            "titre": "Quelques amis"
        },
        {
            "auteur": "Christophe Alevèque",
            "categorie_id": 2,
            "date_publication": "Mon, 04 Oct 2021 00:00:00 GMT",
            "editeur": " Cerf ›",
            "id": 6,
            "isbn": "978-2-2041-4664-7",
            "titre": "Eloge du vieux con moderne"
        },
        {
            "auteur": " Laurent Ruquier",
            "categorie_id": 2,
            "date_publication": "Wed, 05 May 2021 00:00:00 GMT",
            "editeur": " Flammarion ›",
            "id": 7,
            "isbn": " 978-2-0802-5605-8",
            "titre": "Finement Con"
        },
        {
            "auteur": "François Morel",
            "categorie_id": 2,
            "date_publication": "Thu, 07 Oct 2021 00:00:00 GMT",
            "editeur": " Denoël ›",
            "id": 8,
            "isbn": "978-2-2071-6431-0",
            "titre": "Ça va aller !: Chroniques 2019 - 2020"
        }
    ],
    "success": true,
    "total_livres": 7
}

. ## DELETE/categorie)

    GENERAL:
        Delete the categorie of the given ID if it exists. Return the id of the deleted categorie, success value, total of (books) a

        Results are paginated in groups of 25. include a request argument to choose page number, starting from 1.

        SAMPLE: curl -X DELETE http://localhost:5000/categories/25
```
       
```
. ##PATCH/livres/id
  GENERAL:
  This endpoint is used to update a primary_color of plant
  We return a livre(book) which we update

  SAMPLE.....For Patch
  ``` curl -X PATCH http://localhost:5000/livres/42-H "Content-Type:application/json" -d "{"titre": "Peter punk au pays des merveilles"}"
  ```
  ```
  {
    "livre": {
        "auteur": "Laurent Gaulet",
        "categorie_id": 1,
        "date_publication": "Thu, 10 Feb 2022 00:00:00 GMT",
        "editeur": " First ›",
        "id": 3,
        "isbn": "978-2-2651-5546-6",
        "titre": "Officiel de l'humour 2022 : + de 1 500 blagues 100 % fous rires"
    },
    "success modify": true
}
    ```

. ## POST/categories

    GENERAL:    
    This endpoint is used to create a new plant or to search for a plant in relation to the terms contained in the livres(books).
    When the searchTerm parameter is passed from the json, the endpoint performs the search. Otherwise, it is the creation of a new question.
    In the case of the creation of a new question:
    We return the ID of the new plant created, the plant that was created, the list of plant and the number of livres(books).

    SAMPLE.....For Search:
    ```
    curl -X POST http://localhost:5000/categories -H "Content-Type:application/json" -d "{"search":"title"}"
    ```

                

    SAMPLE.....For create

    curl -X POST http://localhost:5000/categories -H "Content-Type:application/json" -d "{"id": 24,"libelle_categorie": "Ma beauté legendaire"}"
```{
    "added": {
        "id": 6,
        "libelle_categorie": "Humour"
    },
    "success": true,
    "total_categorie": 6
}
   
```      


## Testing
To run the tests, run
```
dropdb livres_database
createdb livres_database
psql livres_database_test < livres_database.sql
python test_flaskr.py
```
