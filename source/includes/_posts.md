#Posts

## Create a post

```shell
curl http://localhost:3000/posts 
  -X POST 
  -F "content=user_admin@gmail.com" 
  -F "post_type=Room" 
  -F "post_status=Booked" 
  -F "post_images_attributes[1][image]=/path/to/image.ext" 
  -F "post_images_attributes[1][description]=a description" 
```

> The above command returns, along with the required auth headers, JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "id": 50,
    "user_id": "1",
    "content": "Post new",
    "created_at": "2017-10-26T09:41:42.229Z",
    "updated_at": "2017-10-26T09:41:42.229Z",
    "user_name": "Prasanna Mishra",
    "post_type": null,
    "post_status": null,
    "comment_count": 0,
    "post_images": [
      {
        "description": "this is an iasfasdfmage",
        "url": "/uploads/post_image/image/5/gitlab.png"
      },
      {
        "description": null,
        "url": "/uploads/post_image/image/6/gitlab.svg"
      }
    ]
  }
}
```

This endpoint creates a post by the user logged in.

### Content Type
`multipart/form-data`

### HTTP Request

`POST http://localhost:3000/posts`

### Parameters

Parameter | Description
--------- | -----------
content | Content of the post.
post_type | Type of post [one of `Room`, `Job` and `Announcement`].
post_status | Status of post [one of `Booked` and `Available`].
post_images_attributes[n][image] | n = 1...number of images uploaded, seperate image and description for each image.
post_images_attributes[n][description] | n = 1...number of images uploaded, seperate image and description for each image.

## All Posts

```shell
curl http://localhost:3000/posts?page=1
```

> The above command returns, along with the required auth headers, JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "post_count": 53,
    "posts": [
      {
        "id": 53,
        "user_id": "1",
        "content": "Post new",
        "created_at": "2017-10-26T11:03:53.731Z",
        "updated_at": "2017-10-26T11:03:53.731Z",
        "user_name": "Prasanna Mishra",
        "post_type": null,
        "post_status": null,
        "comment_count": 0,
        "post_images": [
          {
            "description": "this is an iasfasdfmage",
            "url": "/uploads/post_image/image/9/gitlab.png"
          },
          {
            "description": null,
            "url": "/uploads/post_image/image/10/gitlab.svg"
          }
        ]
      },
      {
        "id": 52,
        "user_id": "1",
        "content": "user_admin@gmail.com",
        "created_at": "2017-10-26T09:51:38.878Z",
        "updated_at": "2017-10-26T09:51:38.878Z",
        "user_name": "Prasanna Mishra",
        "post_type": "Room",
        "post_status": "Booked",
        "comment_count": 0,
        "post_images": [
          {
            "description": null,
            "url": null
          }
        ]
      }, 
      ".....",
      "10 posts"
    ]
  }
}
```

This endpoint lists all posts.

### HTTP Request

`GET http://localhost:3000/posts?page=n`

### Query Parameters

Parameter | Optional | Description
--------- | ---------|----------
page | true | page number of posts, each page consists of 10 posts, returns first page if null

## Posts by Status

```shell
curl http://localhost:3000/posts/status/Booked?page=1
```

> The above command returns, along with the required auth headers, JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "post_count": 19,
    "posts": [
      {
        "id": 52,
        "user_id": "1",
        "content": "user_admin@gmail.com",
        "created_at": "2017-10-26T09:51:38.878Z",
        "updated_at": "2017-10-26T09:51:38.878Z",
        "user_name": "Prasanna Mishra",
        "post_type": "Room",
        "post_status": "Booked",
        "comment_count": 0,
        "post_images": [
          {
            "description": null,
            "url": null
          }
        ]
      },
      {
        "id": 24,
        "user_id": "4",
        "content": "post by user 4 of type room and status booked",
        "created_at": "2017-09-08T05:57:58.488Z",
        "updated_at": "2017-09-08T05:57:58.488Z",
        "user_name": null,
        "post_type": "Room",
        "post_status": "Booked",
        "comment_count": 4,
        "post_images": []
      },
      "...",
      "10 posts"
    ]
  }
}
```

This endpoint lists all posts.
<aside class="warning"><code>Deprication Warning!</code> This endpoint will be depricated soon.</aside>

### HTTP Request

`GET http://localhost:3000/posts/status/:post_status?page=n`

### Query Parameters

Parameter | Optional | Description
--------- | ---------|----------
page | true | page number of posts, each page consists of 10 posts, returns first page if null

### URL Parameters

Parameter  | Description
--------- |----------
post_status | Status of post [one of `Booked` and `Available`].

## Posts by Type

```shell
curl http://localhost:3000/posts/type/Room?page=1
```

> The above command returns, along with the required auth headers, JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "post_count": 9,
    "posts": [
      {
        "id": 52,
        "user_id": "1",
        "content": "user_admin@gmail.com",
        "created_at": "2017-10-26T09:51:38.878Z",
        "updated_at": "2017-10-26T09:51:38.878Z",
        "user_name": "Prasanna Mishra",
        "post_type": "Room",
        "post_status": "Booked",
        "comment_count": 0,
        "post_images": [
          {
            "description": null,
            "url": null
          }
        ]
      },
      {
        "id": 24,
        "user_id": "4",
        "content": "post by user 4 of type room and status booked",
        "created_at": "2017-09-08T05:57:58.488Z",
        "updated_at": "2017-09-08T05:57:58.488Z",
        "user_name": null,
        "post_type": "Room",
        "post_status": "Booked",
        "comment_count": 4,
        "post_images": []
      },
      "...",
      "10 posts"
    ]
  }
}
```

This endpoint lists all posts by type.

<aside class="warning"><code>Deprication Warning!</code> This endpoint will be depricated soon.</aside>

### HTTP Request

`GET http://localhost:3000/posts/type/:type?page=n`

### Query Parameters

Parameter | Optional | Description
--------- | ---------|----------
page | true | page number of posts, each page consists of 10 posts, returns first page if null

### URL Parameters

Parameter  | Description
--------- |----------
post_type | type of the required post [one of `Room`, `Job` and `Announcement`].

## Show Post

```shell
curl http://localhost:3000/post/:id
```

> The above command returns, along with the required auth headers, JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "id": 50,
    "user_id": "1",
    "content": "Sample new",
    "created_at": "2017-10-26T09:41:42.229Z",
    "updated_at": "2017-10-26T09:41:42.229Z",
    "user_name": "John Mishra",
    "post_type": null,
    "post_status": null,
    "comment_count": 0,
    "post_images": [
      {
        "description": "this is an iasfasdfmage",
        "url": "/uploads/post_image/image/5/gitlab.png"
      },
      {
        "description": null,
        "url": "/uploads/post_image/image/6/gitlab.svg"
      }
    ]
  }
}
```

This endpoint lists a post.

### HTTP Request

`GET http://localhost:3000/post/:id`

### URL Parameters

Parameter  | Description
--------- |----------
id | id of the required post

## Edit Post

```shell
curl http://localhost:3000/posts/1 
  -X PUT 
  -F "content=user_admin@gmail.com" 
  -F "post_type=Room" 
  -F "post_status=Booked" 
  -F "post_images_attributes[1][image]=/path/to/image.ext" 
  -F "post_images_attributes[1][description]=a description" 
```

> The above command returns, along with the required auth headers, JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "id": 50,
    "user_id": "1",
    "content": "Post new",
    "created_at": "2017-10-26T09:41:42.229Z",
    "updated_at": "2017-10-26T09:41:42.229Z",
    "user_name": "Prasanna Mishra",
    "post_type": null,
    "post_status": null,
    "comment_count": 0,
    "post_images": [
      {
        "description": "this is an iasfasdfmage",
        "url": "/uploads/post_image/image/5/gitlab.png"
      },
      {
        "description": null,
        "url": "/uploads/post_image/image/6/gitlab.svg"
      }
    ]
  }
}
```

This endpoint edits a post by the user logged in.

### Content Type
`multipart/form-data`

### HTTP Request

`POST http://localhost:3000/posts/:id`

### URL Parameters

Parameter  | Description
--------- |----------
id | Id of post to be edited.

### Parameters

Parameter | Description
--------- | -----------
content | Content of the post.
post_type | Type of post [one of `Room`, `Job` and `Announcement`].
post_status | Status of post [one of `Booked` and `Available`].
post_images_attributes[n][image] | n = 1...number of images uploaded, seperate image and description for each image.
post_images_attributes[n][description] | n = 1...number of images uploaded, seperate image and description for each image.

## Delete Post

```shell
curl http://localhost:3000/post/:id
  -X DELETE
```

> The above command returns, along with the required auth headers, JSON structured like this:

```json
{
  "status": "success",
  "data": ""
}
```

This endpoint Deletes a post.

### HTTP Request

`DELETE http://localhost:3000/post/:id`

### URL Parameters

Parameter  | Description
--------- |----------
id | id of the required post