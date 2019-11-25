# Pricing

**Net price** is an amount that does not have taxes included.  
**Gross price** is an amount that already includes a net price + taxes. Examples of this are below in the responses to API calls.

In order to use net pricing in distributor, the "Amount" object, that is returned from the API, has to be used. In every response that has something to do with pricing, the API returns two objects:

1. Old object (Cost) that represents currency and value. This is an old representation and should not be used since it is going to be deprecated by the end of June. After that, API will stop sending it.
2. New object (Amount) that represents a structure that holds both gross and net price. This object is sent always and is the one to be used. It is going to be the only object sent therefore it is mandatory.

Cost object:
```javascript
"GTQ": 540.49
```

In API response it is represented as this:
```javascript
"Total": 
{
  "GTQ": 540.49,
  "RUB": 4433.62
}
```

The new "Amount" structure. This one is the one to be used and supported. 

The object itself has following structure:
```javascript
"GTQ":
{
  "GrossValue": 540.49,
  "NetValue": 540.49,
  "TaxValues": [
    {
      "TaxRateCode": "CZ-Z",
      "Value": 0.00
    }
  ]
}
```

In API response it is represented as this:
```javascript
{
    "TotalAmount": {
        "GTQ": {
            "GrossValue": 540.49,
            "NetValue": 540.49,
            "TaxValues": [
                {
                    "TaxRateCode": "CZ-Z",
                    "Value": 0.00
                }
            ]
        },
        "RUB": {
            "GrossValue": 4433.62,
            "NetValue": 4433.62,
            "TaxValues": [
                {
                    "TaxRateCode": "CZ-Z",
                    "Value": 0.00
                }
            ]
        }
    }
}
```
This "TotalAmount" object will be sent from the API together with the "Total" object. Because the one that should be used has "Amount" in its name, the "Total" object should be ignored.
Be aware that the API responses can be quite large - more about that later.  

Following is an example request for pricing

Request:
```javascript
{
    "HotelId": "...",
    "LanguageCode": "en-GB",
    "StartUtc": "2019-12-25T00:00:00.000Z",
    "EndUtc": "2019-12-26T00:00:00.000Z",
    "RoomCategoryId": "...",
    "ProductIds": [],
    "Occupancies": [
        {
            "AdultCount": 1,
            "ChildCount": 1
        }
    ],
    "Client": "...",
    "Session": "..."
}
```

Response:
```javascript
{
    "OccupancyPrices": [
        {
            "Pricing": [
                {
                    "RateId": "2744408c-a97e-459a-b6b6-ab0400f650b0",
                    "Price": {
                        "Total": {
                            "USD": 100.00,
                            "GBP": 100.00
                        },
                        "TotalAmount": {
                            "USD": {
                                "GrossValue": 100.00,
                                "NetValue": 93.46,
                                "TaxValues": [
                                    {
                                        "TaxRateCode": "DE-R",
                                        "Value": 6.54
                                    }
                                ]
                            },
                            "GBP": {
                                "GrossValue": 100.00,
                                "NetValue": 93.46,
                                "TaxValues": [
                                    {
                                        "TaxRateCode": "DE-R",
                                        "Value": 6.54
                                    }
                                ]
                            }
                        }
                    }
                }
            ],
            "AdultCount": 1,
            "ChildCount": 1
        }
    ]
}
```

**Net pricing**
In the response, NetValue and TaxValues are the ones to be used.  
**Gross pricing**
In the response, GrossValue is the one to be used.

