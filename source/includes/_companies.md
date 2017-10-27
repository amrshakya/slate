#Companies

##Create a Company

```shell
curl http://localhost:3000/companies 
  -X POST 
  -F "name=user_admin@gmail.com" 
  -F "address=Room" 
  -F "longitude=Booked" 
  -F "latitude=Booked" 
  -F "description=Booked" 
  -F "phone=Booked" 
  -F "email=Booked" 
  -F "website=Booked" 
  -F "of_type=Booked" 
  -F "keyline=Booked" 
  -F "opening_time=Booked" 
  -F "closing_time=Booked" 
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