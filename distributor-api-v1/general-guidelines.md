# General Guidelines

## Usage  <a id="Usage"></a>

Distributor API is a public API with no authorization that is designed to be consumed directly by frontend clients. It is unsuitable for continuous polling by a single server due to the built in anti-scraping protection and such requests can fail. For server to server communication, please refer to [Connector API](https://mews-systems.gitbook.io/connector-api/)

## Requests  <a id="requests"></a>

The API accepts only`HTTP POST`requests with`Content-Type`set to`application/json`and JSON content depending on the operation to be performed. All operations follow this address pattern:

```text
[PlatformAddress]/api/distributor/v1/[Resource]/[Operation]
```

* **PlatformAddress**
  * Base address of the MEWS platform, depends on environment \(testing, staging, production\).
* **Resource**
  * Logical group of operations, in most cases identifies target of the operations.
* **Operation**
  * Name of the operation to be performed.

### Body <a id="body"></a>
```javascript
{
    "Client": "My Client 1.0.0",
    "LanguageCode": null,
    "CultureCode": null 
}
```
|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Client` | string | required | Identification of the client as described in [Authorization](authorization.md). |
| `LanguageCode` | string | optional | Code of the language. |
| `CultureCode` | string | optional | Code of the culture. |

All operations of the API require Client to be present in the request.
All operations of the API optionally accept `LanguageCode` and `CultureCode`. These can be used to enforce language and culture of the operation which affects e.g. names of entities, descriptions or error messages. Both of these values must be defined together otherwise default values of the [Enterprise](operations.md#enterprise) are used.

## Responses  <a id="responses"></a>

The API responds with`Content-Type`set to`application/json`and JSON content. In case of success, the HTTP status code is 200 and the content contains result according to the call. In case of error, there are multiple HTTP status codes for different types of errors:

* **400 Bad Request**
  * Error caused by the client app, e.g. in case of malformed request or invalid identifier of a resource. In most cases, such an error signifies a bug in the client app \(consumer of the API\).
* **401 Unauthorized**
  * Error caused by usage of invalid access token.
* **403 Forbidden**
  * Server error that should be reported to the end user of the client app. Happens for example when the server-side validation fails or when a business-logic check is violated.
* **500 Internal Server Error**
  * Unexpectced error of the server. In most cases, such an error signifies a bug on our side. We are logging it and immediately notified when such error happens. If anything like this happens, feel free to directly contact us or raise an issue here on Github.

In case of any error, the returned JSON object describes the error and has the following properties:

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Message` | string | required | Description of the error. |
| `Details` | string | optional | Additional details about the error \(request, headers, server stack trace, inner exceptions etc.\). Only available on development environment. |

Some errors may also contain additional information relevant to the error on top of this two properties. But that depends on the operation and is specificly described in the operation documentation.

## How to support payment cards in custom Distributor client

As part of creating your own custom Distributor client you may want to have a form within your client where customers can enter their payment card data and send this data to Distributor API for further use. Payment card data can then be used by Mews in several ways for example for charging the customer.

To do that some Distributor API endpoints support or require [CreditCardData](operations.md#creditcarddata) (represents payment card data with name `CreditCardData` for legacy and compatibility reasons) in the request. You can visit [Operations](operations.md) to see which endpoints they are.

To send the correct [CreditCardData](operations.md#creditcarddata) you need (check the [docs](operations.md#creditcarddata) to see which fields are required):
* Card holder name
* Card number
* CVV
* Expiration date

This is the relation between the human readable names and the field names which Distributor API uses:

| Human readable      | Distributor API       |
| :------------------ | :-------------------- |
| Card holder name    | `HolderName`          |
| Card number         | `PaymentGatewayData`  |
| Expiration date     | `Expiration`          |
| CVV                 | `PaymentGatewayData`  |

`Expiration` and `HolderName` are not sensitive data in terms of PCI DSS and plain text can be used. The `Expiration` does need to follow the format described in [CreditCardData](operations.md#creditcarddata).

[PaymentGatewayData](payment-gateway-data.md) is a string representing some card data (CVV and card number) which are encoded via payment card storage provider. Those card data are sensitive in terms of PCI DSS and therefore the implementation should not handle them in plain text. 

### To add payment cards support

Please be aware that names of fields in PCI Proxy and Distributor API differ but they represent the same things:

| Distributor API      | PCI Proxy       |
| :-----------------   | :------------   |
| `PublicKey`          | `merchantId`    |
| `PaymentGatewayData` | `transactionId` |

* Confirm that property supports PCI Proxy by checking the field [PaymentCardStorageType](operations.md#paymentcardstoragetype) in Distributor API response. Also read docs about [PaymentGateway](operations.md#payment-gateway) to see what other API data you could potentially use for your implemention.
* Use [PublicKey](operations.md#payment-gateway) as `merchantId` and PCI Proxy with their [guide](https://docs.pci-proxy.com/collect-and-store-cards/capture-iframes) to handle the sensitive card data and to obtain `PaymentGatewayData`.
⚠️  PCI Proxy documentation only highlights the sandbox endpoints. If you want to have access to the production endpoint, you have too omit the `sandbox.` part from the address.
* Use `transactionId` from PCI Proxy as `PaymentGatewayData` inside [CreditCardData](operations.md#creditcarddata). 
 
| Distributor API Field | Used in         | Source          |
| :-----------------    | :------------   | :-----          |
| `PublicKey`           | PCI Proxy       | Distributor API |
| `PaymentGatewayData`  | Distributor API | PCI Proxy       |

