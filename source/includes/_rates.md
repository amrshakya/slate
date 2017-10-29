#Rates

These are the rates of companies (flight rates and exchange rates). Rates are nested in companies, so all operations on rates need the respective company ID.

##Create a Rate

```shell
curl http://localhost:3000/companies/:company_id/rates \
  -X POST \
  -F "description=this is a description" \ 
  -F "price=300" 
```

> The above command returns, along with the required auth headers, JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "id": 21,
    "name": "user_admin@gmail.com",
    "address": "Sydney",
    "description": "asdfh adf hdfasdf a aladjf sladfjladhfjlka hd",
    "website": "www.google.com",
    "keyline": "Booked valways",
    "email": "jon@doe.duh",
    "phone": "9746321987",
    "of_type": "Flight",
    "rate_count": 4,
    "latest_rate": {
      "id": 5,
      "description": "this is a description",
      "price": "300",
      "created_at": "2017-10-29T06:44:32.489Z",
      "updated_at": "2017-10-29T06:44:32.489Z",
      "company_id": 21,
      "user_id": 1
    },
    "opening_time": "9:00",
    "closing_time": "18:00",
    "rates": [
      {
        "id": 5,
        "description": "this is a description",
        "price": "300",
        "updated_at": "2017-10-29T06:44:32.489Z",
        "type": "Flight"
      },
      "... other rates"
    ],
    "users": []
  }
}

```

This endpoint creates a rate on a company.

### HTTP Request

`POST http://localhost:3000/companies/:company_id/rates`

### Parameters

Parameter | Description
--------- | -----------
description | Self Explanatory.
price | Exchange rate of 1AUD if company type = exchange, price of plane ticket in AUD if type is Flight.

### URL Parameters

Parameter  | Description
--------- |----------
company_id | ID of the company on which the rate is to be added.

##Update a Rate

```shell
curl http://localhost:3000/companies/:company_id/rates \
  -X PUT \
  -F "description=this is a description" \ 
  -F "price=300" 
```

> The above command returns, along with the required auth headers, JSON structured like this:

```json
{
  "status": "success",
  "data": [
    {
      "id": 2,
      "description": "",
      "price": "400",
      "updated_at": "2017-10-29T06:43:10.416Z",
      "type": "Flight"
    },
    {
      "id": 3,
      "description": "",
      "price": "403",
      "updated_at": "2017-10-29T06:43:20.398Z",
      "type": "Flight"
    },
    {
      "id": 4,
      "description": "",
      "price": "203",
      "updated_at": "2017-10-29T06:43:24.352Z",
      "type": "Flight"
    },
    {
      "id": 5,
      "description": "this is a description",
      "price": "30023",
      "updated_at": "2017-10-29T06:53:12.118Z",
      "type": "Flight"
    }
  ]
}

```

This endpoint updates a rate on a company and returns all the rates of that company.

### HTTP Request

`PUT http://localhost:3000/companies/:company_id/rates`

### Parameters

Parameter | Description
--------- | -----------
description | Self Explanatory.
price | Exchange rate of 1AUD if company type = exchange, price of plane ticket in AUD if type is Flight.

### URL Parameters

Parameter  | Description
--------- |----------
company_id | ID of the company on which the rate is to be added.

##All Rates

```shell
curl http://localhost:3000/companies/:company_id/rates?page=1 
```

> The above command returns, along with the required auth headers, JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "rate_count": 4,
    "rates": [
      {
        "id": 5,
        "description": "this is a description",
        "price": "300",
        "updated_at": "2017-10-29T06:44:32.489Z",
        "type": "Flight"
      },
      {
        "id": 4,
        "description": "",
        "price": "203",
        "updated_at": "2017-10-29T06:43:24.352Z",
        "type": "Flight"
      },
      {
        "id": 3,
        "description": "",
        "price": "403",
        "updated_at": "2017-10-29T06:43:20.398Z",
        "type": "Flight"
      },
      {
        "id": 2,
        "description": "",
        "price": "400",
        "updated_at": "2017-10-29T06:43:10.416Z",
        "type": "Flight"
      }
    ]
  }
}

```

This endpoint lists all rates of a company paginated.

### HTTP Request

`GET http://localhost:3000/companies/:company_id/rates?page=1`

### URL Parameters

Parameter  | Description
--------- |----------
company_id | ID of the company.

### Query Parameters

Parameter | Optional | Description
--------- | ---------|----------
page | true | page number of rates, each page consists of 6 rates, returns first page if null


