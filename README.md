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
    "id": "59f87c655b1dc209f10c0048",
    "username": "Frank",
    "post_type": "story",
    "post_title": "Student Guide 102",
    "post_text": "Good  stuff",
    "post_url": "http://www.google.com",
    "hanesst_id": 23,
    "post_parent": -1
}

```

An example of a comment:

```javascript

{
    "id": "57f87c655b1dc209f10c6527",
    "username": "BunnyTheRabbit",
    "post_type": "comment",
    "post_title": "The Worlds Greatest Title",
    "post_text": "Awesome commnt text",
    "post_url": "http://www.yahoo.com",
    "hanesst_id": 26,
    "post_parent": 23
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

