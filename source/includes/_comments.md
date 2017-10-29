#Comments

Comments are nested in posts, so all operations on comments need the respective post ID.

##Create a Comment

```shell
curl http://localhost:3000/post/:post_id/comments \
  -X POST \
  -F "content=this is a comment" 
```

> The above command returns, along with the required auth headers, JSON structured like this:

```json
{
  "status": "success",
  "data": [
    {
      "id": 77,
      "content": "comment by user_member@gmail.com on post 5",
      "created_at": "2017-09-08T05:57:58.997Z",
      "updated_at": "2017-09-08T05:57:58.997Z",
      "user_name": null
    },
    {
      "id": 97,
      "content": "New Comment",
      "created_at": "2017-10-29T05:30:23.889Z",
      "updated_at": "2017-10-29T05:30:23.889Z",
      "user_name": "Prasanna Mishra"
    },
    {
      "id": 98,
      "content": "New Comment",
      "created_at": "2017-10-29T05:32:21.152Z",
      "updated_at": "2017-10-29T05:32:21.152Z",
      "user_name": "Prasanna Mishra"
    }
  ]
}

```

This endpoint creates a comment on a post.

### HTTP Request

`POST http://localhost:3000/posts/:post_id/comments`

### Parameters

Parameter | Description
--------- | -----------
comtent | Content of the comment.

### URL Parameters

Parameter  | Description
--------- |----------
post_id | ID of the post on which the comment is to be made.

##All Comments

```shell
curl http://localhost:3000/post/:post_id/comments 
```

> The above command returns, along with the required auth headers, JSON structured like this:

```json
{
  "status": "success",
  "data": [
    {
      "id": 77,
      "content": "comment by user_member@gmail.com on post 5",
      "created_at": "2017-09-08T05:57:58.997Z",
      "updated_at": "2017-09-08T05:57:58.997Z",
      "user_name": null
    },
    {
      "id": 97,
      "content": "New Comment",
      "created_at": "2017-10-29T05:30:23.889Z",
      "updated_at": "2017-10-29T05:30:23.889Z",
      "user_name": "Prasanna Mishra"
    },
    {
      "id": 98,
      "content": "New Comment",
      "created_at": "2017-10-29T05:32:21.152Z",
      "updated_at": "2017-10-29T05:32:21.152Z",
      "user_name": "Prasanna Mishra"
    },
    "... all comments on the post"
  ]
}

```

This endpoint lists all comments on a post.

### HTTP Request

`GET http://localhost:3000/posts/:post_id/comments`

### URL Parameters

Parameter  | Description
--------- |----------
post_id | ID of the post.

##Deleting a comment

```shell
curl http://localhost:3000/post/:post_id/comments/:comment_id
  -X DELETE
```

> The above command returns, along with the required auth headers, JSON structured like this:

```json
{
  "status": "success",
  "data": ""
}

```

This endpoint deletes a comment on a post.

### HTTP Request

`DELETE http://localhost:3000/posts/:post_id/comments/:comment_id`

### URL Parameters

Parameter  | Description
--------- |----------
post_id | ID of the post.
comment_id | ID of the comment.