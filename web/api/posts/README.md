# `posts`
### GET `/posts`
**Description:**
Grabs all posts data

**Example:**

Input:
```bash
$ GET /posts
```

Output:
```javascript
{
    "status": "SUCCESS",
    "data": [
        {
            "id": 1,
            "title": "Welcome to Kville ",
            "body": "Welcome to Kville. Remember Black tenting will start promptly at 11pm on Saturday, January 12th.  See you there Crazies!!",
            "created_at": "2019-01-11T17:02:06.075Z",
            "updated_at": "2019-01-11T17:02:06.075Z"
        },
        {
            "id": 2,
            "title": "Grace Period",
            "body": "The weather is lower than 25 degrees today. congrats no night shift!!!!",
            "created_at": "2019-01-13T00:12:00.528Z",
            "updated_at": "2019-01-13T00:12:00.528Z"
        },
        ...
        {
            "id": 11,
            "title": "Good News!",
            "body": "Grace for the whole week!",
            "created_at": "2019-01-29T05:05:40.888Z",
            "updated_at": "2019-01-29T05:05:40.888Z"
        }
    ]
}
```

### GET `/posts/:id`
**Description:**
Get single post by ID of post

**Example:**

Input:
```bash
$ GET /posts/1
```

Output:
```javascript
{
    "status": "SUCCESS",
    "data": {
            "id": 1,
            "title": "Welcome to Kville ",
            "body": "Welcome to Kville. Remember Black tenting will start promptly at 11pm on Saturday, January 12th.  See you there Crazies!!",
            "created_at": "2019-01-11T17:02:06.075Z",
            "updated_at": "2019-01-11T17:02:06.075Z"
        }
}
```


### POST `/posts
**Description:**
Create a post. Needs a `title` and `body` string in the request data.

**Example:**

Input:
```bash
POST /posts

{ 
  title: "New Post",
  body: "Test",
}
```

Output: 
```javascript
{
    "status": "SUCCESS",
    "message": "Post created successfully.",
    "data": {
        "id": 12,
        "title": "New Post",
        "body": "Test",
        "created_at": "2019-11-17T00:09:36.142Z",
        "updated_at": "2019-11-17T00:09:36.142Z"
    }
}
```

### PUT `/posts/:id`
**Description:**
Update a post by ID of post. Needs a `title` and `body` string in the request data.

**Example:**
Input:
```bash
POST /posts/1

{
  title: "Sicko Mode",
  body: "Sicko Sicko Mode 2"
}
```

Output:
```javascript
{
    "status": "SUCCESS",
    "message": "Post updated successfully.",
    "data": {
        "id": 1,
        "title": "Sicko Mode",
        "body": "Sicko Sicko Mode 2",
        "created_at": "2019-11-15T20:21:04.120Z",
        "updated_at": "2019-11-17T00:10:23.199Z"
    }
}
```

### DELETE `/posts/:id`
**Description:**
Delete a post by ID of post. 

**Example:**
Input:
```bash
DELETE /posts/1
```

Output:
```
{
    "status": "SUCCESS",
    "message": "Post deleted successfully.",
}
```
