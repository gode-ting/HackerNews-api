# HackerNews API

This is a simple api for a todo list app. It contains basic CRUD operations and handles user authentication and authorization.
</br>
</br>

## Installation

clone the repository

```sh

$ cd to/your/favorite/path

$ git clone https://github.com/emilgras/simple-flask-auth.git

$ cd simple-flask-aut

```

create and activate a local virtual environment

```sh

$ python3 -m venv venv

$ source venv/bin/activate

```

Install dependencies from `requirements.txt`

```sh

(venv) $ pip install -r requirements.txt

```
</br>

## Running the project

Start the python interpreter and create the database

```sh

(venv) $ python

>>> from api import db

>>> db.create_all()

>>> exit()

```

(optional) Start the sqlite3 command line and verify that 2 tables has been created `user` & `todo`

```sh

(venv) $ sqlite3

>>> .tables

```

Exit the sqlite command line

```sh

>>> .exit

```
Start the application 

```sh

(venv) $ python api.py

```
</br>

## Items

Stories, comments, jobs, Ask HNs and even polls are just items. They're identified by their ids, which are unique integers. All items have some of the following properties:

| Field | Description |
| --- | --- |
| id | The item's unique id. |
| type | The type of item. i.e. "story, comment, poll" |
| username | The username of the item's author |
| text | The comment, story or poll |
| parent | The comment's parent id. The parent could be  another comment or a story |
| url | The URL of the story |
| title | The title of the story, poll or job |
</br>  

An example of a story:

```javascript

{
  "by" : "dhouston",
  "descendants" : 71,
  "id" : 8863,
  "kids" : [ 8952, 9224, 8917, 8884, 8887, 8943, 8869, 8958, 9005, 9671, 8940, 9067, 8908, 9055, 8865, 8881, 8872, 8873, 8955, 10403, 8903, 8928, 9125, 8998, 8901, 8902, 8907, 8894, 8878, 8870, 8980, 8934, 8876 ],
  "score" : 111,
  "time" : 1175714200,
  "title" : "My YC app: Dropbox - Throw away your USB drive",
  "type" : "story",
  "url" : "http://www.getdropbox.com/u/2/screencast.html"
}

```

## Endpoints

Authentication routes

| Method | Endpoint | Description |
| --- | --- | --- |
| POST | /login | log's in a user |
| POST | /register | creates a new user with no access token |
</br>

Admin routes

| Method | Endpoint | Description | Parameters | Result |
| --- | --- | --- | --- | --- |
| GET | /user | get all users | --- | list of users | 
| GET | /user/<public_id> | get a single user | `public_id` | single user |
| PUT | /user/<public_id> | promote user to admin | `public_id` | --- |
| DELETE | /user/<public_id> | deletes a user | `public_id` | --- |
</br>

Todo routes

| Method | Endpoint | Description | Parameters | Result |
| --- | --- | --- | --- | --- |
| GET | /todo | get all users | --- | list of todo items | 
| GET | /todo/<todo_id> | get a single todo item | `public_id` | todo item |
| PUT | /todo/<todo_id> | complete todo item | `todo_id` | --- |
| DELETE | /todo/<todo_id> | deletes todo item | `public_id` | --- |

