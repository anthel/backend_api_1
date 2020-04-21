# Intro:
**https://api.softhouse.rocks** <br>
An API that implements jsonplaceholder post and users endpoints, backed by a mongo database.

The purpose for this API is educational and meant as a step between using jsonplaceholder in a UI and implementing your own API.

## The HTTP Methods supported are:
- GET
- POST
- PUT
- PATCH

## Supported but you need Auth:
- DELETE

### Method: GET
##### Example with endpoint: **/posts**:<br>
curl -i -H "Content-Type:application/json" http://api.softhouse.rocks/posts/1

Gets the information in the specified URI

**The result will look like this:**<br>
{"_id":"5e806d9f42fbde006b6b9ecf","userId":1,"id":1,"title":"sunt aut facere repellat provident occaecati excepturi optio reprehenderit","body":"quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto","__v":0}

##### Example2:<br>
curl -X GET http://api.softhouse.rocks/posts/1 | jq .

Gets the information in the specified URI and displays it in JSON format

**The result will look like this:**
{
  "_id": "5e9ecdbd3c9c34a2d807ce9d",
  "id": 1,
  "__v": 0,
  "body": "string",
  "title": "string",
  "userId": 1
}

### Method: POST
##### Example with endpoint: **/posts**:<br>
curl -i -X POST -H "Content-Type:application/json" http://api.softhouse.rocks/posts -d '{"title":"Hi, World", "body":"Fresh as morning dew", "userId": "1"}' 

The Curl above POSTs to the softhouse api: "Title", "Body", "userId".

**The result will look like this:**
{"_id":"5e9eb17e09cee0002106f314","body":"Fresh as morning dew","title":"Hi, World","userId":1,"id":811,"__v":0}

**With jq:**
{
  "_id": "5e9eadf3a8eb15002609e47b",
  "body": "Fresh as morning dew",
  "title": "Hi, World",
  "userId": 1,
  "id": 807,
  "__v": 0
}


### Method: PUT

##### Example:
curl -i -X PUT http://api.softhouse.rocks/posts/3 -H "Content-Type:application/json" -d  '{
  "body": "NewBody", "title": "NewTitle", "userId": "1337"}'

  Replaces the information on the specified path, with the provided data

##### Result:
Status: 200 OK

Returns body with the old information, should look like this

{"_id":"5e9ed8353c9c34a2d807f465","id":3,"__v":0,"body":"OldBody","title":"OldTitle","userId":13}



### Method: PATCH

##### Example:
curl -i -X PATCH http://api.softhouse.rocks/posts/3 -H "Content-Type:application/json" -d  '{
  "body": "newBody", "userId": "3"}'

  Updates a part of the object on the specified path, depending on the provided data

##### Result:
Status: 200 OK

Returns body with the updated information

"body": "newBody", "title": "oldTitle", userId": "3"



### Method: DELETE

#### Example:
curl -i -X DELETE http://api.softhouse.rocks/posts/1

Deletes an object or endpoint at the specified path

#### Result:

Status: If path was found and was succesfully deleted, returns code 200 OK.
If path not found and nothing was found, returns 204 No Content
