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

## User authentication endpoints

Authentication

| Method | Endpoint | Description |
| --- | --- | --- |
| POST | /login | Login a user |
| POST | /signup | Sign up a new user |
</br>

Signup example:

```sh
curl -H "Content-Type: application/json" -X POST -d '{
    "username" : "username",
    "password" : "password"
}'  http://{ip_address}:{port_number}/signup
```

Login Example

```sh
curl -H "Content-Type: application/json" -X POST -d '{
    "username" : "username",
    "password" : "password"
}'  http://{ip_address}:{port_number}/login
```

When you log in successfully you will receive a Token in the response header looking like this `Authorization: Bearer  xxx.yyy.zzz`

Important `/signup` status codes

| Code | Description |
| --- | --- |
| 200 | Success |
| 400 | Bad crednetials. User entered incorrect input |
| 500 | Server error |

Important `/login` status codes

| Code | Description |
| --- | --- |
| 200 | Success |
| 401 | Bad credentials. Incorrect username or password |
| 500 | Server error |

## Post endpoints

| Nr. | Method | Endpoint | Description | Return body |
| --- | --- | --- | --- | --- |
| 1 | GET | /post?page=<page_number> | Get all posts. | List og post objects. If no results you receive an empty list. |
| 2 | GET | /post/<post_id> | Get single post by id | Single post object |
| 3 | POST | /post | Create new post | void |
| 4 | PUT | /post/<post_id> | Update post by id | void |
| 5 | DELETE | /post//<post_id> | Deletes post by id | void |
</br>

Example 1 - Get all posts:

Obs: You have to specify the page number starting from 1. Default page size is 20. This way you can make use of paging to optimze perfomance of your website.

```sh
curl -H "Content-Type: application/json" -X POST -d '{
    "username" : "username",
    "password" : "password"
}'  http://{ip_address}:{port_number}/users/signup
```

Example 2 - Get single post by id:

```sh
curl -H "Content-Type: application/json" -X POST -d '{
    "username" : "username",
    "password" : "password"
}'  ht
```

Example 3 - Get single post by id:

```sh
curl -H "Content-Type: application/json" -X POST -d '{
    "username" : "username",
    "password" : "password"
}'  ht
```

Example 4 - Get single post by id:

```sh
curl -H "Content-Type: application/json" -X POST -d '{
    "username" : "username",
    "password" : "password"
}'  ht
```

Example 5 - Get single post by id:

```sh
curl -H "Content-Type: application/json" -X POST -d '{
    "username" : "username",
    "password" : "password"
}'  ht
```
