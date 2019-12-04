# Pricing

* **Net price** is an amount without taxes.
* **Gross price** is a net price + taxes.

In order to use pricing in the Distributor, the API returns the [Amount](pricing.md#amount) object as part of responses.
[Amount](pricing.md#amount) represents a structure that holds gross price, net price and tax values.

The [Amount](pricing.md#amount) has following structure:

```javascript
{
    "USD":
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
}
```

### Amount

| Property | Type | Description |
| :--- | :--- | :--- |
| `GrossValue` | Number | Gross value  |
| `NetValue` | Number | Net value |
| `TaxValues` | Collection of [TaxValue](pricing.md#taxvalue)s | Tax values for the net value amount |

### TaxValue

| Property | Type | Description |
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

This "TotalAmount" object will be sent from the API and it will contain values for every currency which is represented by [Amount](pricing.md#amount). TotalAmount is dictionary with Currency as a key and [Amount](pricing.md#amount) as value.
