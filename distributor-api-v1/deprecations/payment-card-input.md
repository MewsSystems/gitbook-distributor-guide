# PaymentCardInput deprecation
[PaymentCardInput](#paymentcardinput) field of [configuration](../operations.md#configuration) object is deprecated and will be removed from the response of [configuration/get](../operations.md#getconfigurationinfo) on 31.7.2021. It is replaced by [PaymentCardRequirement](#paymentcardrequirement). The new field contains two new options for requiring a payment card.

## Response diff

```diff
{
    "Cities": [
        {
            "Id": "9044b0bf-cbe0-4df5-beeb-b32e19bcd073",
            "ImageId": "e956201e-ba2f-470f-8070-b43f9cd72194",
            "Name": {
                "en-US": "Amsterdam"
            }
        }
    ],
    "CityId": "9044b0bf-cbe0-4df5-beeb-b32e19bcd073",
    "Configurations": [
        {
            "Id": "3edbe1b4-6739-40b7-81b3-d369d9469c48",
            "AdultCount": null,
            "ChildCount": null,
            "ChildSelectionEnabled": null,
            "CompetitorRateDescription": {
                    "en-US": "Comptetitor Rate Description"
                },
            "CompetitorPriceRelativeAdjustment": 1.1,
            "DisplayAvailability": null,
            "DisplayPromoCode": null,
            "DisplayRateComparision": null,
            "DisplaySpecialRequests": null,
            "Enterprise": {
                "AcceptedCurrencyCodes": ["EUR"],
                "AdditionalLegalStatements": {
                    "en-US": "Lorem ipsum."
                },
                "Address": {
                    "City": "Zeist",
                    "CountryCode": "NL",
                    "Latitude": 52.0749748,
                    "Line1": "Arnhemse Bovenweg 31",
                    "Line2": "",
                    "Longitude": 5.2590181,
                    "PostalCode": "3708 AA"
                },
                "Categories": [
                    {
                        "Description": {
                            "en-US": "Our Single Castleroom is a cozy and comfortable room with a single bed (80x200), spacious bathroom with guest supplies, working desk and a flat screen TV. This quiet non-smoking room of 15m2 has a nice view of the Castle and of course there is free high speed Wi-Fi.\r\n"
                        },
                        "ExtraBedCount": 0,
                        "Id": "295d96e7-8501-4cbd-b78d-8bf590bf6db9",
                        "ImageIds": ["f987a97c-5049-44ca-9933-5b657e5263e2"],
                        "Name": {"en-US": "Single Castleroom"},
                        "NormalBedCount": 1,
                        "Ordering": 0,
                        "SpaceType": "Room"
                    }
                ],
                "CityId": "39db0c2f-6929-47ec-9386-0abdaaef4c9c",
                "DefaultCurrencyCode": "EUR",
                "DefaultLanguageCode": "nl-NL",
                "DefaultRateCurrencyCode": "EUR",
                "Description": {"nl-NL": ""},
                "Email": "info@kasteelkerckebosch.com",
                "IanaTimeZoneIdentifier": "Europe\/Berlin",
                "Id": "7a13590c-6538-461e-b02f-6357400de493",
                "ImageId": "263c3e5f-e11d-41d8-9746-4bdd0852f04f",
                "IntroImageId": "f24469f8-c23b-4450-a1f8-3ecd39904e99",
                "Name": {
                    "en-US": "Sample Hotel Description"
                },
                "Pricing": "Gross",
                "PrivacyPolicyUrl": {
                    "en-US": "https://localhost/en"
                },
                "Products": [
                    {
                        "Id": "1627aea5-8e0a-4371-9022-9b504344e724",
                        "Amounts": {
                            "EUR": {
                                "GrossValue": 5.00,
                                "NetValue": 4.5,
                                "TaxValues": [
                                    {
                                        "TaxRateCode": "DE-R",
                                        "Value": 0.5
                                    }
                                ]
                            },
                            "CZK": {
                                "GrossValue": 150.00,
                                "NetValue": 140.00,
                                "TaxValues": [
                                    {
                                        "TaxRateCode": "DE-R",
                                        "Value": 10.00
                                    }
                                ]
                            }
                        },
                        "CategoryId": null,
                        "Charging": "Once",
                        "Description": {
                            "en-US": "Continental breakfast served in the morning."
                        },
                        "ImageId": "1627aea5-8e0a-4371-9022-9b504344e724",
                        "IncludedByDefault": false,
                        "Name": {
                            "en-US": "Breakfast"
                        },
                        "Ordering": 0,
                        "Posting": "Once",
                        "RelativePrice": null
                    }
                ],
                "TaxEnvironmentCode": "NL",
                "Telephone": "030 6926666",
                "TermsAndConditionsUrl": {
                    "en-US": "https://website.com/terms-and-conditions.html"
                }
            },
            "OnlineTravelAgencies": [],
-           "PaymentCardInput": "NotRequested",
+           "PaymentCardRequirement": "NotRequired",
            "RequiredFields": [],
            "ServiceId": "c1eec12a-1101-4bg6-ad24-e48f8dlpb9ee"
        }
    ],
    "CurrencyCode": null,
    "CurrencyCodes": [],
    "DisplayVoucherCode": false,
    "EndDateOffset": null,
    "GtmContainerId": "",
    "IntroVideoUrl": "",
    "LanguageCode": null,
    "NowUtc": "2020-04-09T07:18:48Z",
    "PrimaryColor": "",
    "StartDateOffset": null,
    "Theme": null,
    "VoucherCode": ""
}
```

### PaymentCardInput
* `NotRequested` - Payment card info is not requested.
* `Requested` - Payment card info is requested, but not validated.
* `Required` - Payment card info is requested and validated.

### PaymentCardRequirement
* `NotRequired` - Payment card info is never required. 
* `AlwaysRequired` - Payment card info is always required and validated.
* `NotRequiredForFullyPaidBookings` - Payment card info is not required for fully paid bookings. Otherwise required.
* `NotRequiredForFullyOrPartiallyPaidBookings` - Payment card info is not required for fully or partially paid bookings. Otherwise required.