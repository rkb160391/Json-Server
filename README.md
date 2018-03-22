# Json-Server
With the help of json-server we can develop or test Angular Application. There is no hard and fast rule to having a real server for developing or tasting an Angular project.




Create a db.json file

{
  "posts": [
    { "id": 1, "title": "json-server", "author": "typicode" }
  ],
  "comments": [
    { "id": 1, "body": "some comment", "postId": 1 }
  ],
  "profile": { "name": "typicode" }
}

Install
$ npm install -g json-server

Start JSON Server
$ json-server --watch db.json
Now if you go to http://localhost:3000/posts/1, you'll get

{ "id": 1, "title": "json-server", "author": "typicode" }
Also when doing requests, it's good to know that:

If you make POST, PUT, PATCH or DELETE requests, changes will be automatically and safely saved to db.json using lowdb.
Your request body JSON should be object enclosed, just like the GET output. (for example {"name": "Foobar"})
Id values are not mutable. Any id value in the body of your PUT or PATCH request wil be ignored. Only a value set in a POST request wil be respected, but only if not already taken.
A POST, PUT or PATCH request should include a Content-Type: application/json header to use the JSON in the request body. Otherwise it will result in a 200 OK but without changes being made to the data.

Routes
Based on the previous db.json file, here are all the default routes. You can also add other routes using --routes.

Plural routes
GET    /posts
GET    /posts/1
POST   /posts
PUT    /posts/1
PATCH  /posts/1
DELETE /posts/1
Singular routes
GET    /profile
POST   /profile
PUT    /profile
PATCH  /profile
Filter
Use . to access deep properties

GET /posts?title=json-server&author=typicode
GET /posts?id=1&id=2
GET /comments?author.name=typicode
