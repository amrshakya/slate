#Exchange Rates

These are different from rates of companies. These are shown on the main app screen updated by admin.

##All Exchange Rates

```shell
curl http://localhost:3000/exchange_rates 
```

> The above command returns, along with the required auth headers, JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "ticks": [
      {
        "id": 21,
        "day": "2017-09-04",
        "rate": "6",
        "created_at": "2017-09-08T05:57:59.208Z",
        "updated_at": "2017-09-08T05:57:59.208Z"
      },
      {
        "id": 22,
        "day": "2017-09-05",
        "rate": "7",
        "created_at": "2017-09-08T05:57:59.213Z",
        "updated_at": "2017-09-08T05:57:59.213Z"
      },
      {
        "id": 23,
        "day": "2017-09-06",
        "rate": "3",
        "created_at": "2017-09-08T05:57:59.217Z",
        "updated_at": "2017-09-08T05:57:59.217Z"
      },
      {
        "id": 24,
        "day": "2017-09-07",
        "rate": "1",
        "created_at": "2017-09-08T05:57:59.223Z",
        "updated_at": "2017-09-08T05:57:59.223Z"
      },
      {
        "id": 25,
        "day": "2017-09-08",
        "rate": "5",
        "created_at": "2017-09-08T05:57:59.229Z",
        "updated_at": "2017-09-08T05:57:59.229Z"
      }
    ],
    "avg": 4.4
  }
}

```

This endpoint lists 5 ticks of exchange rates and an average of the 5 ticks (no average if less than 5 ticks).

### HTTP Request

`GET http://localhost:3000/exchange_rates`

