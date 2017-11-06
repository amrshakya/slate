#Companies

##Create a Company

```shell
curl http://localhost:3000/companies \
  -X POST \
  -F "name=user_admin@gmail.com" \
  -F "address=Sydney" \
  -F "longitude=63.32.36" \
  -F "latitude=52.32.32" \
  -F "description=asdfh adf hdfasdf a aladjf sladfjladhfjlka hd" \
  -F "phone=9746321987" \
  -F "email=jon@doe.duh" \
  -F "website=www.google.com" \
  -F "of_type=Flight" \
  -F "keyline=Booked valways" \
  -F "opening_time=9:00" \
  -F "closing_time=18:00" \
```

> The above command returns, along with the required auth headers, JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "address": "Sydney",
    "closing_time": "18:00",
    "description": "asdfh adf hdfasdf a aladjf sladfjladhfjlka hd",
    "email": "jon@doe.duh",
    "id": 21,
    "keyline": "Booked valways",
    "latest_rate": null,
    "name": "user_admin@gmail.com",
    "of_type": "Flight",
    "opening_time": "9:00",
    "phone": "9746321987",
    "rate_count": 0,
    "rates": [],
    "users": [],
    "website": "www.google.com"
  }
}

```

This endpoint creates a company.

### HTTP Request

`POST http://localhost:3000/companies`

### Parameters

Parameter | Description
--------- | -----------
name | Name of the company.
address | Self explanatory
latitude | Self explanatory
longitude | Self explanatory
description | Self explanatory
phone | Self explanatory
email | Self explanatory
website | Self explanatory
of_type | One of `Exchange` and `Flight`
keyline | Self explanatory
opening_time | Self explanatory
closing_time | Self explanatory

## All Companies

```shell
curl http://localhost:3000/companies
```

> The above command returns, along with the required auth headers, JSON structured like this:

```json
{
  "status": "success",
  "data": [
    {
      "id": 21,
      "name": "user_admin@gmail.com",
      "address": "Sydney",
      "description": "asdfh adf hdfasdf a aladjf sladfjladhfjlka hd",
      "website": "www.google.com",
      "keyline": "Booked valways",
      "email": "jon@doe.duh",
      "phone": "9746321987",
      "of_type": "Flight",
      "rate_count": 0,
      "latest_rate": null,
      "opening_time": "9:00",
      "closing_time": "18:00",
      "rates": [],
      "users": []
    },
    {
      "id": 20,
      "name": "Company1",
      "address": "Aus",
      "description": "this is a standard descriptopn",
      "website": null,
      "keyline": "no keyline is our keyline",
      "email": "fuck@you",
      "phone": "9841 aru no aafai han",
      "of_type": "baje",
      "rate_count": 0,
      "latest_rate": null,
      "opening_time": "rati sute paxi",
      "closing_time": "bihana uthna agadi",
      "rates": [],
      "users": [
        {
          "id": 1,
          "email": "user_admin@gmail.com",
          "name": "Prasanna Mishra",
          "image": null,
          "roles": [
            "admin"
          ],
          "admin": true
        },
        {
          "id": 5,
          "email": null,
          "name": "Will Warmanwitz",
          "image": null,
          "roles": [
            "member"
          ],
          "admin": false
        }
      ]
    },
    "... all companies"
  ]
}
```

This endpoint lists all companies.

### HTTP Request

`GET http://localhost:3000/companies`

### Query Parameters

Parameter | Optional | Description
--------- | ---------|----------
page | true | page number of companies, each page consists of 10 posts, returns all if null
of_type | true | status of post, one of ` 0 => Exchange, 1 => Flight `
name | true | searches wuth name LIKE input
email | true |  searches wuth email LIKE input
address | true |  searches wuth address LIKE input
phone | true |  searches wuth phome LIKE input
created_between | true | searched for records created between `start_date` and `end_date`. Send as a hash `?created_between[start_date]=YYYY-MM-DD&created_between[end_date]=YYYY-MM-DD`

## Companies by Type

```shell
curl http://localhost:3000/companies/type/Flight
```

> The above command returns, along with the required auth headers, JSON structured like this:

```json
{
  "status": "success",
  "data": [
    {
      "id": 21,
      "name": "user_admin@gmail.com",
      "address": "Sydney",
      "description": "asdfh adf hdfasdf a aladjf sladfjladhfjlka hd",
      "website": "www.google.com",
      "keyline": "Booked valways",
      "email": "jon@doe.duh",
      "phone": "9746321987",
      "of_type": "Flight",
      "rate_count": 0,
      "latest_rate": null,
      "opening_time": "9:00",
      "closing_time": "18:00",
      "rates": [],
      "users": []
    },
    {
      "id": 20,
      "name": "user_admin@gmail.com",
      "address": "Room",
      "description": "Booked",
      "website": "Booked",
      "keyline": "Booked",
      "email": "Booked",
      "phone": "Booked",
      "of_type": "Flight",
      "rate_count": 0,
      "latest_rate": null,
      "opening_time": "Booked",
      "closing_time": "Booked",
      "rates": [],
      "users": []
    },
    "... all companies of type"
  ]
}
```

This endpoint lists all companies by type.

<aside class="warning"><code>Deprication Warning!</code> This endpoint will be depricated soon.</aside>

### HTTP Request

`GET http://localhost:3000/companies/type/:type`

### Query Parameters

Parameter | Optional | Description
--------- | ---------|----------
page | true | page number of companies, each page consists of 6 companies, returns all if null

### URL Parameters

Parameter  | Description
--------- |----------
type | type of the required company [one of `Flight` and `Exchange`].
