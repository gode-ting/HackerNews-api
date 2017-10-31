# HackerNews API

This is a simple api for a todo list app. It contains basic CRUD operations and handles user authentication and authorization.
</br>
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

## Status codes



## User Endpoints

Authentication

| Method | Endpoint | Description | Status code on success |
| --- | --- | --- | --- |
| POST | /login | Login a user | 200 |
| POST | /users/signup | Sign up a new user | 200 |
</br>

Signup example:

```sh
curl -H "Content-Type: application/json" -X POST -d '{
    "username" : "username",
    "password" : "password"
}'  http://{ip_address}:{port_number}/users/signup
```

Login Example

```sh
curl -H "Content-Type: application/json" -X POST -d '{
    "username" : "username",
    "password" : "password"
}'  http://{ip_address}:{port_number}/login
```

Important authentication http status codes

| Code | Description |
| --- | --- |
| 200 | Success |
| 400 | Bad credentials. Credentials are not correctly formatted |
| 500 | Internal server error |

## Post endpoints

| Method | Endpoint | Description | Parameters | Result |
| --- | --- | --- | --- | --- |
| GET | /user | get all users | --- | list of users | 
| GET | /user/<public_id> | get a single user | `public_id` | single user |
| PUT | /user/<public_id> | promote user to admin | `public_id` | --- |
| DELETE | /user/<public_id> | deletes a user | `public_id` | --- |
</br>

Signup example:

```sh
curl -H "Content-Type: application/json" -X POST -d '{
    "username" : "username",
    "password" : "password"
}'  http://{ip_address}:{port_number}/users/signup
```

Login Example

```sh
curl -H "Content-Type: application/json" -X POST -d '{
    "username" : "username",
    "password" : "password"
}'  ht

