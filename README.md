# Hacker News API

This is the Hacker News api containing detailed description on how to inertact with the api.
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
    "post_parent": 23
}

```  

## User authentication endpoints

Authentication

| Nr. | Method | Endpoint | Description |
| --- | --- | --- | --- |
| 1 | POST | /login | Login a user |
| 2 | POST | /user/signup | Sign up a new user |
</br>

Example 1 - Signup:

```sh
curl -H "Content-Type: application/json" -X POST -d '{
    "username" : "username",
    "password" : "password"
}'  http://{ip_address}:{port_number}/signup
```

Example 2 - Login

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

| Nr. | Method | Endpoint | Description | Return body | Requires authentication |
| --- | --- | --- | --- | --- | --- |
| 1 | GET | /post?page=<page_number> | Get all posts. | List og post objects. If no results you receive an empty list. | No |
| 2 | GET | /post?id=<post_id> | Get single post by id and all child posts | Single post object and a list of comments if any | No |
| 2 | GET | /post?username=<username> | Get user by username | Single user | No |
| 3 | POST | /post | Create new post | void | Yes |
| 4 | PUT | /post/<post_id> | Update post by id | void | Yes |
| 5 | DELETE | /post//<post_id> | Deletes post by id | void | Yes |
</br>

Example 1 - Get all posts:

Obs: You have to specify the page number starting from 1. Default page size is 20. Every page request will return 20 or less posts. This way you can optimze perfomance of your website.

```sh
curl http://<ip-address>:<post>/post?page=1
```

Example 2 - Get single post by id:

```sh
curl http://<ip-address>:<post>/post?id=dqwdh12e8ewdwjshjk
```

Example 3 - Create new post:

Obs: Remeber to switch the token to a valid token. The one provided will not work

```sh
curl -H "Content-Type: application/json" -H @{'Authorization'='Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJ1c2VybmFtZSIsImV4cCI6MTUxMDM0MjU0NiwidXNlcm5hbWUiOiJ1c2VybmFtZSJ9.wpBvdhT8-wsp4GfuTIrROCHjK6Vp1ySXJZpNFLT9xcvSQcAPDNLHXkHdc-RPaZC7fwPOlvdFkgrRz1DbEa03sj'} -X POST -d '{
	"post_title": "My crazy awesome title here", 
	"post_text": "", 
	"post_type": "story", 
	"post_parent": -1,
	"post_url": "http://www.google.com"
}'  http://<ip-address>:<post>/post
```

Example 4 - Update post by id:

```sh
curl -H "Content-Type: application/json" -X PUT -d '{
    "post_title": "New awesome title"
}'  http://<ip-address>:<post>/post?id=q38w4fyiesldhflskedfhk
```

Example 5 - Delete post by id:

```sh
curl -X DELETE http://<ip-address>:<post>/post?id=982347r87whf47xcf
```
