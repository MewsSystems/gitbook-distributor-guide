# Pricing

**Net price** is an amount without taxes.  
**Gross price** is a net price + taxes.

In order to use net pricing in distributor, the API returns the [Amount](net-pricing.md#Amount) object as part of responses.
[Amount](net-pricing.md#Amount) represents a structure that holds gross price, net price and tax values.

The Amount has following structure:
```javascript
Currency:
{
    "GrossValue": 100.00,
	"NetValue": 93.46,
	"TaxValues": [
		{
			"TaxRateCode": "DE-R",
			"Value": 6.54
		}
	]
}
```

### Amount <a id="amount"></a>

|  | Property | Description |
| :--- | :--- | :--- |
| `GrossValue` | Number | Gross value  |
| `NetValue` | Number | Net value |
| `TaxValues` | [TaxValue](net-pricing.md.md#taxValue) | Tax value for the net value amount |

### TaxValue <a id="taxValue"></a>
|  | Property | Description |
| :--- | :--- | :--- |
| `TaxRateCode` | string | Unique identifier of the rate. |
| `Value` | Number | Amount of tax |


In API response it is represented as this:
```javascript
{
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
		"GrossValue": 90.00,
		"NetValue": 83.46,
		"TaxValues": [
			{
				"TaxRateCode": "DE-R",
				"Value": 6.54
			}
		]
	}
    }
}
```
This "TotalAmount" object will be sent from the API and it will contain values for every currency which is represented by [Amount](net-pricing.md#Amount). TotalAmount is dictionary with Currency as a key and [Amount](net-pricing.md#Amount) as value.

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
    "Client": "...",
    "Session": "...",
    "Occupancies": [
        {
            "AdultCount": 1,
            "ChildCount": 1
        }
    ]
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
                                "GrossValue": 90.00,
                                "NetValue": 83.46,
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
