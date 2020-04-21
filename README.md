# Intro:
**https://api.softhouse.rocks**
An API that implements jsonplaceholder post and users endpoints, backed by a mongo database.

The purpose for this API is educational and meant as a step between using jsonplaceholder in a UI and implementing your own API.

# The HTTP Methods supported are:
## GET, POST

## Supported but you need Auth:
## DELETE

### Method: GET
##### Example:
curl -i -H "Content-Type:application/json" http://api.softhouse.rocks/posts/1

**The result will look like this:**
{"_id":"5e806d9f42fbde006b6b9ecf","userId":1,"id":1,"title":"sunt aut facere repellat provident occaecati excepturi optio reprehenderit","body":"quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto","__v":0}

### Method: POST
##### Example:
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


