# Operations

## Get Configuration Info   <a id="get-configuration-info"></a>

Preferred initial call used to obtain all static data about distributor configuration for the client.

### Request`[PlatformAddress]/api/distributor/v1/configuration/get`   <a id="request-platformaddressapidistributorv1hotelsget"></a>

```javascript
{
    "Client": "My Client 1.0.0",
    "Ids": [
        "3edbe1b4-6739-40b7-81b3-d369d9469c48",
        ...
    ],
    "PrimaryId": "3edbe1b4-6739-40b7-81b3-d369d9469c48"
}
```

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Client` | string | required | Identification of the client as described in [Authorization](https://mews-systems.gitbook.io/distributor-guide/distributor-api-v1/authorization). |
| `PrimaryId` | string | required | Primary configuration id. |
| `Ids` | array of strings | required | List of configuration ids. |

### Response   <a id="response-platformaddressapidistributorv1configuratioget"></a>

```javascript
{
    "Cities": [
        {
            "Id": "9044b0bf-cbe0-4df5-beeb-b32e19bcd073",
            "ImageId": "e956201e-ba2f-470f-8070-b43f9cd72194",
            "Name": { 
                "ru-RU": "Амстердам", 
                "en-US": "Amsterdam"
            },
        },
    ],
    "CityId": "9044b0bf-cbe0-4df5-beeb-b32e19bcd073",
    "Configurations": [
        {
            "AdultCount": null,
            "ChildCount": null,
            "ChildSelectionEnabled": null,
            "DisplayAvailability": null,
            "DisplayPromoCode": null,
            "DisplayRateComparision": null,
            "DisplaySpecialRequests": null,
            "Enterprise": {
                "AcceptedCurrencyCodes":["EUR"],
                "AdditionalLegalStatements":[],
                "Address": {
                    "City":"Zeist",
                    "CountryCode":"NL",
                    "Latitude":52.0749748,
                    "Line1":"Arnhemse Bovenweg 31",
                    "Line2":"",
                    "Longitude":5.2590181,
                    "PostalCode":"3708 AA"
                },
                "Categories":[
                    {
                        "Description": {
                            "en-US":"Our Single Castleroom is a cozy and comfortable room with a single bed (80x200), spacious bathroom with guest supplies, working desk and a flat screen TV. This quiet non-smoking room of 15m2 has a nice view of the Castle and of course there is free high speed Wi-Fi.\r\n"
                        },
                        "ExtraBedCount":0,
                        "Id":"295d96e7-8501-4cbd-b78d-8bf590bf6db9",
                        "ImageIds":["f987a97c-5049-44ca-9933-5b657e5263e2"],
                        "Name": {"en-US":"Single Castleroom"},
                        "NormalBedCount":1,
                        "SpaceType":"Room"
                    }
                ],
                "CityId":"39db0c2f-6929-47ec-9386-0abdaaef4c9c",
                "DefaultCurrencyCode":"EUR",
                "DefaultLanguageCode":"nl-NL",
                "DefaultRateCurrencyCode":"EUR",
                "Description":{"nl-NL":""},
                "Email":"info@kasteelkerckebosch.com",
                "IanaTimeZoneIdentifier":"Europe\/Berlin",
                "Id":"7a13590c-6538-461e-b02f-6357400de493",
                "ImageId":"263c3e5f-e11d-41d8-9746-4bdd0852f04f",
                "IntroImageId":"f24469f8-c23b-4450-a1f8-3ecd39904e99",
                "Name":{
                    "en-US": "Sample Hotel Description"
                },
                "Products":[
                    {
                        "AlwaysIncluded":false,
                        "CategoryId":null,
                        "Charging":"Once",
                        "Posting":"Once",
                        "Description": {
                            "en-US": "Continental breakfast served in the morning."
                        },
                        "Id": "1627aea5-8e0a-4371-9022-9b504344e724",
                        "ImageId": "1627aea5-8e0a-4371-9022-9b504344e724",
                        "IncludedByDefault":false,
                        "Ordering":0,
                        "Name": {
                            "en-US": "Breakfast"
                        },
                        "Prices": {
                            "EUR": 5,
                            "CZK": 150
                        }
                        "RelativePrice":null
                    }
                ],
                "Telephone":"030 6926666",
                "TermsAndConditionsUrl": "https://website.com/terms-and-conditions.html"
            },
            "Id": "3edbe1b4-6739-40b7-81b3-d369d9469c48",
            "OnlineTravelAgencies": [],
            "PaymentGatewayEnabled": false,
        }
    ],
    "CurrencyCode": null,
    "CurrencyCodes": [],
    "EndDateOffset": null,
    "GtmContainerId": "",
    "IntroVideoUrl: "",
    "LanguageCode": null,
    "NowUtc": "",
    "PrimaryColor": "",
    "StartDateOffset": null,
    "Theme": null,
    "VoucherCode": null,
    "DisplayVoucherCode": null,
}
```

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Cities` | array of [City](operations.md#city) | required | Cities supported by hotel. |
| `CityId` | string | required | ID of default city. |
| `Configurations` | array of [Configuration](operations.md#configuration) | required | Configurations matching the configuration IDs in request. |
| `CurrencyCode` | string | optional | Code of default currency accepted by hotel. |
| `Currencies` | array of [Currency](operations.md#currency) | required | Currencies accepted by hotel. |
| `EndDateOffset` | string | optional | TBC |
| `GtmContainerId` | string | optional | Google tag manager indentifier. |
| `IntroVideoUrl` | string | optional | TBC |
| `LanguageCode` | string | optional | Code of default language. |
| `NowUtc` | string | required | Server UTC date and time. |
| `PrimaryColor` | string | optional | TBC |
| `StartDateOffset` | string | optional | TBC |
| `Theme` | string | optional | TBC |
| `VoucherCode` | string | optional | TBC |

## Get Hotel Info   <a id="get-hotel-info"></a>

Alternative initial call used to obtain all static data about hotel relevant for the client.

### Request`[PlatformAddress]/api/distributor/v1/hotels/get`   <a id="request-platformaddressapidistributorv1hotelsget"></a>

```javascript
{
    "Client": "My Client 1.0.0",
    "HotelId": "3edbe1b4-6739-40b7-81b3-d369d9469c48"
}
```

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Client` | string | required | Identification of the client as described in [Authorization](https://mews-systems.gitbook.io/distributor-guide/distributor-api-v1/authorization). |
| `HotelId` | string | required | Unique identifier of hotel. |

### Response   <a id="response"></a>

```javascript
{
    "Languages": [
        {
            "Code": "en-US",
            "Name": "English (United States)",
            "DefaultCulture": {
                "CurrencyDecimalSeparator": ",",
                "CurrencyGroupSeparator": "."
            }
        }
    ],
    "Currencies": [
        {
            "Code": "CZK",
            "Symbol": "Kč",
            "ValueFormat": "#,##0 \"Kč\";−#,##0 \"Kč\"",
            "DecimalPlaces": 0,
            "SymbolIsBehindValue": true
        }
    ],
    "Countries": [
        {
            "Code": "CZ",
            "Name": "Czech Republic"
        }
    ],
    "ImageBaseUrl": "https://cdn.demo.mews.li/Media/Image",
    "Id": "3edbe1b4-6739-40b7-81b3-d369d9469c48",
    "Name": {
        "en-US": "Distributor api hotel"
    },
    "Description": {
        "en-US": ""
    },
    "CityId": "e5fd108e-1e0a-4cc4-9d3a-34d7e0e57527",
    "ImageId": "87ead9b6-8c96-4b3c-a90d-fb8a02a005ad",
    "IntroImageId": "c0dcec83-96a4-44b5-a898-de2becbbdb5e",
    "DefaultLanguageCode": "en-US",
    "DefaultCurrencyCode": "EUR",
    "DefaultRateCurrencyCode": "EUR",
    "SupportedLanguageCodes": [
        "cs-CZ",
        "da-DK",
        "de-CH",
        "de-DE",
        "el-GR",
        "en-GB",
        "ta-IN",
        "tr-TR",
        "uk-UA",
        "en-US"
    ],
    "AcceptedCurrencyCodes": [
        "CZK",
        "EUR",
        "USD"
    ],
    "RoomCategories": [
        {
            "Id": "d79fa529-d95e-485e-b81b-e8a669a1062a",
            "Name": {
                "en-US": "King Double Room"
            },
            "Description": {
                "en-US": "The double rooms have two separate beds, 2 x 105 wide."
            },
            "ImageIds": [],
            "Ordering": 4,
            "NormalBedCount": 2,
            "ExtraBedCount": 0,
            "SpaceType": "Room"
        }
    ],
    "Products": [
        {
            "Id": "5d6de830-8ada-4b65-b72c-60fc1e719f1b",
            "Name": {
                "nl-NL": "Extra bedlinnen",
                "en-US": "Extra bedlinnen (Once Off)"
            },
            "Description": {},
            "CategoryId": "77e0a18c-f2a5-418f-b578-16d3599c059d",
            "ImageId": "ec643f33-cd6c-4250-accd-518182165ffe",
            "IncludedByDefault": false,
            "AlwaysIncluded": false,
            "Prices": {
                "CZK": 258,
                "EUR": 10,
            },
            "RelativePrice": null,
            "Charging": "Once",
            "Posting": "Once",
            "Ordering": 0
        }
    ],
    "PaymentGateway": {
        "PaymentGatewayType": "PciProxy",
        "IsMerchant": true,
        "SupportedCreditCardTypes": [
            "MasterCard",
            "Visa",
            "Amex"
        ],
        "PublicKey": "1100016827"
    },
    "TermsAndConditionsUrl": "https://demo.mews.li/Commander/Home/TermsAndConditions/3edbe1b4-6739-40b7-81b3-d369d9469c48",
    "IanaTimeZoneIdentifier": "Europe/Budapest",
    "Email": "distributor-api@mews.li",
    "Telephone": "+",
    "AdditionalLegalStatements": [],
    "Address": {
        "Line1": "Staromestske namesti 16",
        "Line2": "",
        "City": "Prague",
        "PostalCode": "11000",
        "CountryCode": "US",
        "Latitude": null,
        "Longitude": null
    }
}
```

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Countries` | array of [Country](operations.md#country) | required | Countries supported by hotel. |
| `Currencies` | array of [Currency](operations.md#currency) | required | Currencies accepted by hotel. |
| `DefaultCurrencyCode` | string | required | Code of hotel’s default currency. |
| `DefaultLanguageCode` | string | required | Code of hotel’s default language. |
| `DefaultRateCurrencyCode` | string | required | Code of currency of hotel’s default rate. |
| `IanaTimezoneIdentifier` | string | required | Iana identifier of hotel’s time zone |
| `ImageId` | string | optional | Unique identifier of hotel’s logo image. |
| `IntroImageId` | string | optional | Unique identifier of hotel’s intro image \(usable as background image\). |
| `Languages` | array of [Language](operations.md#language) | required | Languages supported by the hotel. |
| `Name` | [LocalizedText](operations.md#localizedtext) | required | Name of the hotel. |
| `Description` | [LocalizedText](operations.md#localizedtext) | required | Description of the hotel. |
| `PaymentGateway` | one of [PaymentGateway ](operations.md#payment-gateway)types | optional | Info about payment gateway used by the hotel. |
| `Products` | array of [Product](operations.md#product) | required | All products orderable with rooms. |
| `RoomCategories` | array of [RoomCategory](operations.md#roomcategory) | required | All room categories offered by hotel. |
| `TermsAndConditionsUrl` | string | optional | URL of hotel’s terms and conditions. |
| `ImageBaseUrl` | string | required | Base URL of images. |

### API Response entites   <a id="entities"></a>

#### City   <a id="city"></a>

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Id` | string | required | City identifier. |
| `ImageId` | string | optional | Identifier of image assigned to city. |
| `Name` | string | required | Name of the city. |

#### Configuration   <a id="configuration"></a>

TBC

#### Country   <a id="country"></a>

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Code` | string | required | ISO 3166-1 Aplha-2 code of the country. |
| `Name` | string | required | Name of the country. |

#### Currency   <a id="currency"></a>

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Code` | string | required | Code of the currency in the ISO format. |
| `Symbol` | string | required | Symbol of the currency. |
| `ValueFormat` | string | required | Format of a currency value \(for both positive and negative values, including symbol\). |
| `DecimalPlaces` | number | required | Number of decimal places used with the currency value. |
| `SymbolIsBehindValue` | boolean | required | Indicates whether the symbol stands behind a value in standard formatting. |

#### Language   <a id="language"></a>

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Code` | string | required | Code of the language in the ISO format. |
| `Name` | string | required | Name of the language. |
| `DefaultCulture` | [Culture](operations.md#culture) | required | Specifics of a default culture for the language. |

#### Culture   <a id="culture"></a>

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `CurrencyDecimalSeparator` | string | required | Symbol used to separate decimal places in the currency value format. |
| `CurrencyGroupSeparator` | string | required | Symbol used to separate thousands in the currency value format. |

#### LocalizedText   <a id="localizedtext"></a>

A localized text is an object of the property values localized into languages supported by hotel, indexed by language codes.

#### Payment Gateway   <a id="payment-gateway"></a>

If the hotel does not use any payment gateway, the value is null. If it does, then you should use a specific api call and the gateway’s library to encode credit card data. The main purpose of a payment gateway is to securely obtain credit card of the customer before a reservation is created. You can decide not to support any of them and just ignore it, in which case reservations are created with note about missing credit card.

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `PaymentGatewayType` | string | required | Type of the payment gateway \(`Adyen`, `Stripe` or `PciProxy`\). |
| `IsMerchant` | boolean | required | Whether the gateway is processed through Mews Merchant or not. |
| `SupportedCreditCardTypes` | array of string | required | The list of supported credit cards, should be used to enhance UX. |

#### Product   <a id="product"></a>

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Id` | string | required | Unique identifier of the product. |
| `CategoryId` | string | optional | Unique identifier of the product category. |
| `Name` | [LocalizedText](operations.md#localizedtext) | required | Name of the product localized into all supported languages. |
| `Description` | [LocalizedText](operations.md#localizedtext) | required | Description of the product localized into all supported languages. |
| `ImageId` | string | optional | Unique identifier of the product’s image. |
| `IncludedByDefault` | boolean | required | Indicates whether the product should be added to order by default. |
| `AlwaysIncluded` | boolean | required | Indicates whether the product is always included \(= cannot be removed\). |
| `Prices` | [CurrencyValues](operations.md#currencyvalues) | required | Price of the product. |

#### CurrencyValues   <a id="currencyvalues"></a>

An object where field names correspond to currency ISO codes and field values to amounts. Only currencies that the hotel accepts are listed, for example:

```javascript
{
    "EUR": 100.00,
    "USD": 120.50,
    "CZK": 2500
}
```

#### RoomCategory   <a id="roomcategory"></a>

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Id` | string | required | Unique identifier of the room category. |
| `Name` | [LocalizedText](operations.md#localizedtext) | required | Name of the room category localized into all supported languages. |
| `Description` | [LocalizedText](operations.md#localizedtext) | required | Description of the room category localized into all supported languages. |
| `ImageIds` | array of strings | required | Unique identifiers of images attached with the room category. |
| `NormalBedCount` | number | required | Number of normal beds in the room category. |
| `ExtraBedCount` | number | required | Number of extra beds possible in the room category. |
| `SpaceType` | string | required | Type of the room category - “Room” or “Bed”. |

## Validate Voucher   <a id="validate-voucher"></a>

Can be used to deterimne whether a voucher code is valid.

### Request`[PlatformAddress]/api/distributor/v1/vouchers/validate`   <a id="request-platformaddressapidistributorv1vouchersvalidate"></a>

```javascript
{
    "Client": "My Client 1.0.0",
    "HotelId": "3edbe1b4-6739-40b7-81b3-d369d9469c48",
    "VoucherCode": "Discount2042"
}
```

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Client` | string | required | Identification of the client as described in [Authorization](https://mews-systems.gitbook.io/distributor-guide/distributor-api-v1/authorization). |
| `HotelId` | string | required | Unique identifier of hotel. |
| `VoucherCode` | string | required | Code of voucher to validate, case sensitive. |

### Response   <a id="response-1"></a>

```javascript
{
    "IsValid": false
}
```

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `IsValid` | boolean | required | Indicates whether the voucher code is valid. |

## Get Availability   <a id="get-availability"></a>

Gives availabilities and pricings for given date interval with product prices included for each room category. Categorized by applicable rates and person counts from 1 to full room. If room category is not available, it is left out from response.

### Request`[PlatformAddress]/api/distributor/v1/hotels/getAvailability`   <a id="request-platformaddressapidistributorv1hotelsgetavailability"></a>

```javascript
{
    "Client": "My Client 1.0.0",
    "HotelId": "3edbe1b4-6739-40b7-81b3-d369d9469c48",
    "StartUtc": "2015-01-01T00:00:00Z",
    "EndUtc": "2015-01-03T00:00:00Z",
    "ProductIds": [
        "d0e88da5-ae64-411c-b773-60ed68954f64"
    ],
    "VoucherCode": "Discount2042",
    "AdultCount": 2,
    "ChildCount": 0,
    "CategoryIds": [
        "295d96e7-8501-4cbd-b78d-8bf590bf6db9"
    ]
}
```

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Client` | string | required | Identification of the client as described in [Authorization](https://mews-systems.gitbook.io/distributor-guide/distributor-api-v1/authorization). |
| `HotelId` | string | required | Unique identifier of hotel. |
| `StartUtc` | string | required | Reservation start date \(arrival date\) in ISO 8601 format. |
| `EndUtc` | string | required | Reservation end date \(departure date\) in ISO 8601 format. |
| `ProductIds` | array of string | optional | Ids of products which should be included into pricing calculations. |
| `VoucherCode` | string | optional | Voucher code enabling special rate offerings. |
| `AdultCount` | number | optional | Requested number of adults. If provided together with `ChildCount`, then `RoomOccupancyAvailabilities` will be computed only for that combination instead of all possible. If `RoomCategory` doesn’t support given values, nearest applicable are found. |
| `ChildCount` | number | optional | Requested number of children. |
| `CategoryIds` | array of string | optional | Ids of categories for which should be the availability computed only. If omitted, availability of all categories is returned instead. |

### Response   <a id="response-2"></a>

```javascript
{
    "Rates": [
        {
            "Id": "c1d48c54-9382-4ceb-a820-772bf370573d",
            "Name": {
                "en-US": "Rate"
            },
            "Description": {
                "en-US": "Best rate available."
            },
            "IsPrivate": false
        }
    ],
    "RoomCategoryAvailabilities": [
        {
            "RoomCategoryId": "4037c0ec-a59d-43f1-9d97-d6c984764e8c",
            "AvailableRoomCount": 5,
            "RoomOccupancyAvailabilities": [
                {
                    "AdultCount": 1,
                    "ChildCount": 0,
                    "Pricing": [
                        {
                            "RateId": "c1d48c54-9382-4ceb-a820-772bf370573d",
                            "Price": { },
                            "MaxPrice": { }
                        }
                    ]
                },
                {
                    "AdultCount": 2,
                    "ChildCount": 0,
                    "Pricing": [
                        {
                            "RateId": "c1d48c54-9382-4ceb-a820-772bf370573d",
                            "Price": {
                                "Total": { },
                                "AveragePerNight": { }
                            },
                            "MaxPrice": {
                                "Total": { },
                                "AveragePerNight": { }
                            }
                        }
                    ]
                }
            ]
        }
    ]
}
```

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Rates` | array of [Rate](operations.md#rate) | required | Information about all available rates. |
| `RoomCategoryAvailabilites` | array of [RoomCategoryAvailability](operations.md#roomcategoryavailability) | required | Availabilities of room categories. If a room category is not available, it is not included. |

#### Rate   <a id="rate"></a>

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Id` | string | required | Unique identifier of the rate. |
| `Name` | [LocalizedText](operations.md#localizedtext) | required | Name of the rate localized into all supported languages. |
| `Description` | [LocalizedText](operations.md#localizedtext) | required | Description of the rate localized into all supported languages. |
| `IsPrivate` | boolean | required | Set to `true` for promotion rate enabled by provided `VoucherCode` |

#### RoomCategoryAvailability   <a id="roomcategoryavailability"></a>

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `RoomCategoryId` | string | required | Unique identifier of the room category. |
| `RoomOccupancyAvailabilities` | array of [RoomOccupancyAvailability](operations.md#roomoccupancyavailability) | required | Availabilities of rooms in the category by the room occupancy. |
| `AvailableRoomCount` | number | required | Number of available rooms from the room category. |

#### RoomOccupancyAvailability   <a id="roomoccupancyavailability"></a>

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `AdultCount` | number | required | Number of adults for the associated pricing. |
| `ChildCount` | number | required | Number of childs for the associated pricing. |
| `Pricing` | array of [Pricing](operations.md#pricing) | required | Pricing information. |

#### Pricing   <a id="pricing"></a>

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `RateId` | string | required | Unique identifier of a rate. |
| `Price` | [RoomPrice](operations.md#roomprice) | required | Price of the room. |
| `MaxPrice` | [RoomPrice](operations.md#roomprice) | required | Max price of the room with the same parameters and conditions among other rates. Can be understood \(and possibly displayed\) as the value before discount. |

#### RoomPrice   <a id="roomprice"></a>

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Total` | [CurrencyValues](operations.md#currencyvalues) | required | Total price of the room for whole reservation. |
| `AveragePerNight` | [CurrencyValues](operations.md#currencyvalues) | required | Average price per night. |

## Get Reservations Pricing   <a id="get-reservations-pricing"></a>

Gives a pricing information for the given configuration.

### Request`[PlatformAddress]/api/distributor/v1/reservations/getPricing`   <a id="request-platformaddressapidistributorv1reservationsgetpricing"></a>

```javascript
{
    "Client": "My Client 1.0.0",
    "HotelId": "3edbe1b4-6739-40b7-81b3-d369d9469c48",
    "StartUtc": "2015-01-01T00:00:00Z",
    "EndUtc": "2015-01-03T00:00:00Z",
    "VoucherCode": "Discount2042",
    "RoomCategoryId": "3540c7d4-e128-41e2-81d8-ff4d196c595a",
    "Occupancies": [
        {
            "AdultCount": 2,
            "ChildCount": 0
        }
    ],
    "ProductIds": [
        "d0e88da5-ae64-411c-b773-60ed68954f64"
    ]
}
```

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Client` | string | required | Identification of the client as described in [Authorization](https://mews-systems.gitbook.io/distributor-guide/distributor-api-v1/authorization). |
| `HotelId` | string | required | Unique identifier of the hotel. |
| `StartUtc` | string | required | Start date of the reservation \(arrival date\). |
| `EndUtc` | string | required | End date of the reservation \(departure date\). |
| `VoucherCode` | string | optional | A voucher code. |
| `RoomCategoryId` | string | required | Identifier of the requested room category. |
| `Occupancies` | array of [Occupancy](operations.md#occupancy) | required | Occupancies of the reservations. |
| `ProductIds` | array of string | optional | Identifiers of the requested products. |

#### Occupancy   <a id="occupancy"></a>

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `AdultCount` | number | required | Number of adults. |
| `ChildCount` | number | required | Number of children. |

### Response   <a id="response-3"></a>

```javascript
{
    "OccupancyPrices": [
        {
            "AdultCount": 1,
            "ChildCount": 0,
            "Pricing": [
                {
                    "MaxPrice": {
                        "AveragePerNight": {},
                        "Total": {}
                    },
                    "Price": {
                        "AveragePerNight": {},
                        "Total": {}
                    },
                    "RateId": "b34330be-7e19-453e-8959-592c4e820f85"
                }
            ]
        }
    ]
}
```

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `OccupancyPrices` | array of [RoomOccupancyAvailability](operations.md#roomoccupancyavailability) | required | Pricing information. |

## Get Payment Gateway   <a id="create-reservation-group"></a>

### Request`[PlatformAddress]/api/distributor/v1/payments/getPaymentGateway`   <a id="request-platformaddressapidistributorv1reservationgroupscreate"></a>

```javascript
{
    "HotelId": "3edbe1b4-6739-40b7-81b3-d369d9469c48",
    "Client": "My Client 1.0.0",
    "Session": "...",
    "LanguageCode": "en-GB",
    "CultureCode": "en-GB"
}
```

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `HotelId` | string | required | Unique identifier of hotel |
| `Client` | string | required | Identification of the client as described in [Authorization](https://mews-systems.gitbook.io/distributor-guide/distributor-api-v1/authorization) |
| `Session` | number | required | Session number |
| `LanguageCode` | string | required | Language code |
| `CultureCode` | string | required | Culture Code |

### Response   <a id="response-5"></a>

```javascript
{
    {
        "PaymentGatewayType": "Adyen",
        "IsMerchant": false,
        "SupportedCreditCardTypes": [
            "MasterCard",
            "Visa"
        ],
        "PublicKey": "..."
    }
}
```

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| PaymentGatewayType | string | required | Type of the payment gateway \(`Adyen`, `Stripe` or `PciProxy`\) |
| IsMerchant | boolean | required | Whether the gateway is processed through Mews Merchant or not |
| SupportedCreditCardTypes | array of strings | required | The list of supported credit cards, should be used to enhance UX |
| PublicKey | string | required | A key used by the payment gateway's client side library for authentication |

## Create Reservation Group   <a id="create-reservation-group"></a>

### Request`[PlatformAddress]/api/distributor/v1/reservationGroups/create`   <a id="request-platformaddressapidistributorv1reservationgroupscreate"></a>

```javascript
{
    "Client": "My Client 1.0.0",
    "HotelId": "3edbe1b4-6739-40b7-81b3-d369d9469c48",
    "Customer": {
        "Email": "hiro@snow.com",
        "FirstName": "Hiro",
        "LastName": "Protagonist",
        "Telephone": "",
        "AddressLine1": "",
        "AddressLine2": "",
        "City": "",
        "PostalCode": "",
        "StateCode": "",
        "NationalityCode": "",
        "SendMarketingEmails": true
    },
    "Booker": {
        "Email": "john.doe@snow.com",
        "FirstName": "John",
        "LastName": "Doe",
        "Telephone": "654257001458"
    },
    "Reservations": [
        {
            "RoomCategoryId": "4037c0ec-a59d-43f1-9d97-d6c984764e8c",
            "StartUtc": "2015-01-01T00:00:00Z",
            "EndUtc": "2015-01-03T00:00:00Z",
            "VoucherCode": "Discount2042",
            "RateId": "c1d48c54-9382-4ceb-a820-772bf370573d",
            "AdultCount": 3,
            "ChildCount": 0,
            "ProductIds": [
                "d0e88da5-ae64-411c-b773-60ed68954f64"
            ],
            "Notes": "Quiet room please."
        }
    ],
    "CreditCardData": {
        "PaymentGatewayData": "...",
        "ObfuscatedCreditCardNumber": "411111******1111",
        "Expiration": "2020-10"
    }
}
```

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Client` | string | required | Identification of the client as described in [Authorization](https://mews-systems.gitbook.io/distributor-guide/distributor-api-v1/authorization). |
| `HotelId` | string | required | Unique identifier of the hotel. |
| `Customer` | [Customer](operations.md#customer) | required | Information about customer who creates the order. |
| `Booker` | [Booker](operations.md#booker) | optional | Information about booker. |
| `Reservations` | array of [ReservationData](operations.md#reservationdata) | required | Parameters of reservations to be ordered. |
| `CreditCardData` | [CreditCardData](operations.md#creditcarddata) | optional | Credit card data, required if hotel has payment gateway. |

#### Customer   <a id="customer"></a>

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Email` | string | required | Email of the customer. |
| `FirstName` | string | required | First name of the customer. |
| `LastName` | string | required | Last name of the customer. |
| `Telephone` | string | optional | Telephone number of the customer. |
| `AddressLine1` | string | optional | First line of the address. |
| `AddressLine2` | string | optional | Second line of the address. |
| `City` | string | optional | City. |
| `PostalCode` | string | optional | Postal code of the address. |
| `StateCode` | string | optional | ISO 3166-2 code of the state, e.g.`US-AL`. |
| `NationalityCode` | string | optional | ISO 3166-1 Aplha-2 code of the customer’s nation country, e.g.`US`. |
| `SendMarketingEmail` | boolean | optional | Subscribe to marketing emails |

#### Booker   <a id="booker"></a>

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Email` | string | required | Email of the booker. |
| `FirstName` | string | required | First name of the booker. |
| `LastName` | string | required | Last name of the booker. |
| `Telephone` | string | optional | Telephone number of the booker. |

#### ReservationData   <a id="reservationdata"></a>

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `RoomCategoryId` | string | required | Identifier of the requested room category. |
| `StartUtc` | string | required | Start date of the reservation \(arrival date\). |
| `EndUtc` | string | required | End date of the reservation \(departure date\). |
| `VoucherCode` | string | optional | A voucher code, set to be paired with reservation for later retrieval only. Actual voucher rate used is determined by setting a proper `RateId`. |
| `RateId` | string | required | Identifier of the chosen rate. |
| `AdultCount` | number | required | Number of adults. |
| `ChildCount` | number | required | Number of children. |
| `ProductIds` | array of string | optional | Identifiers of the requested products. |
| `Notes` | string | optional | Additional notes. |

#### CreditCardData   <a id="creditcarddata"></a>

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `PaymentGatewayData` | string | required | Encoded credit card data obtained from the payment gateway specific library. More details [here](payment-gateway-data.md). |
| `ObfuscatedCreditCardNumber` | string | required | Obfuscated credit card number, e.g.`411111******1111`. |
| `Expiration` | string | required | Expiration of credit card in format `YYYY-MM`. Required with PCI Proxy payment gateway type. |

### Response   <a id="response-6"></a>

```javascript
{
    "Id": "f6fa7e62-eb22-4176-bc49-e521d0524dee",
    "CustomerId": "7ac6ca0d-7c08-4ab1-8da8-9b44979d8855",
    "Reservations": [
        {
            "Id": "123456ec-a59d-43f1-9d97-d6c984764e8c",
            "RoomCategoryId": "4037c0ec-a59d-43f1-9d97-d6c984764e8c",
            "StartUtc": "2015-01-01T00:00:00Z",
            "EndUtc": "2015-01-03T00:00:00Z",
            "RateId": "c1d48c54-9382-4ceb-a820-772bf370573d",
            "Rate": {
                "Id": "c1d48c54-9382-4ceb-a820-772bf370573d",
                "Name": {
                    "en-US": "Rate"
                },
                "Description": {
                    "en-US": "Best rate available."
                }
            },
            "AdultCount": 3,
            "ChildCount": 0,
            "ProductIds": [
                "d0e88da5-ae64-411c-b773-60ed68954f64"
            ],
            "Notes": "Quiet room please.",
            "Cost": { },
            "Number": "1234"
        }
    ],
    "TotalCost": { }
}
```

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Id` | string | required | Unique identifier of the created reservation group. |
| `CustomerId` | string | required | Unique identifier of customer who created reservation group. |
| `Reservations` | array of [Reservation](operations.md#reservation) | required | The created reservations in group. |
| `TotalCost` | [CurrencyValues](operations.md#currencyvalues) | required | Total cost of the whole group. |

### Reservation   <a id="reservation"></a>

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Id` | string | required | Identifier of the reservation. |
| `Number` | string | required | Confirmation number of the reservation. |
| `RoomCategoryId` | string | required | Identifier of the requested room category. |
| `StartUtc` | string | required | Start date of the reservation \(arrival date\). |
| `EndUtc` | string | required | End date of the reservation \(departure date\). |
| `AdultCount` | number | required | Number of adults. |
| `ChildCount` | number | required | Number of children. |
| `ProductIds` | array of string | optional | Identifiers of the requested products. |
| `RateId` | string | required | Identifier of the chosen rate. |
| `Notes` | string | optional | Additional notes. |
| `Cost` | [CurrencyValues](operations.md#currencyvalues) | required | Total cost of the reservation. |

### Error Response   <a id="error-response"></a>

In case of an error caused by insufficient availability \(which might have decreased since the time it was provided to the client\), the error response may contain the following fields on top the standard ones:

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `ExceedingReservationIndexes` | array of number | optional | Indexes of reservations from the request that are not available anymore. |

## Get Reservation Group   <a id="get-reservation-group"></a>

### Request`[PlatformAddress]/api/distributor/v1/reservationGroups/get`   <a id="request-platformaddressapidistributorv1reservationgroupsget"></a>

```javascript
{
    "Client": "My Client 1.0.0",
    "HotelId": "3edbe1b4-6739-40b7-81b3-d369d9469c48",
    "ReservationGroupId": "f6fa7e62-eb22-4176-bc49-e521d0524dee"
}
```

|  | Property | Type | Description |
| :--- | :--- | :--- | :--- |
| `Client` | string | required | Identification of the client as described in [Authorization](https://mews-systems.gitbook.io/distributor-guide/distributor-api-v1/authorization). |
| `HotelId` | string | required | Unique identifier of the hotel. |
| `ReservationGroupId` | string | required | Unique identifier of the reservation group. |

### Response   <a id="response-7"></a>

Same as in [Create Reservation Group](operations.md#create-reservation-group).

