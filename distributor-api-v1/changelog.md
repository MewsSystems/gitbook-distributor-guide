# Changelog

## 29.11.2021

* Changed domain from www.mews.li to api.mews.com
 
## 09.11.2021

* Added [CategoryImageAssignment](./operations.md#category-image-assignment) docs and [deprecated ImageIds in the RoomCategory](./deprecations/README.md).

## 08.03.2021

* Added `AverageAmountPerTimeUnit` field to [Room price](./operations.md#room-price) replacing the `AverageAmountPerNight`.
* Added `ChargingMode` field to [Product](./operations.md#product) replacing the `Charging`.
* Added `PostingMode` field to [Product](./operations.md#product) replacing the `Posting`.
* Added `SettlementMaximumTimeUnits` field to [Rate group](./operations.md#rate-group) replacing the `SettlementMaximumNights`.

## 21.07.2021

* Added `Services` parameter at [Get configuration](./operations.md#get-configuration) endpoint that uses newly added [Service](./operations.md#service) object.

## 10.05.2021

* Fixed inconsistency in naming in the documentation.
* Fixed DTOs table heading to reflect the columns.

## 03.05.2021

* Added use case on [On session payment card authorization](./use-cases/on-session-payment-card-authorization.md).

## 19.04.2021

* Moved use case on [How to support payment card in booking engine client application](./use-cases/how-to-support-payment-cards-in-booking-engine-application.md).

## 30.03.2021

* Added use case for [On session payments](./use-cases/on-session-payments.md).

## 25.03.2021

* Changed naming of URL variables used in the documentation to make clear distinction between application URLs and API URLs.

## 19.03.2021

* Changed urls for testing (demo) environments.

## 26.11.2020

* Changed of [API Client Authorization](./authorization.md). Where the client needs to be registered.

## 20.11.2020

* Made `ConfigurationId` parameter in [Create reservation group](./operations.md#create-reservation-group) endpoint required.
* Added `ConfigurationId` parameter to [Get availability](./operations.md#get-availability) endpoint.
* Previous variant of sending `HotelId` without `ConfigurationId` to these endpoints was deprecated.

## 28.08.2020

* Added `CurrencyCode` parameter to [Get availability](./operations.md#get-availability) endpoint.

## 22.06.2020

* Added section describing payment card support.
* Improved `PaymentGatewayData` description.
* Removed deprecated payment gateways.
* Improved `CreditCardData` description.
* [PR 36](https://github.com/MewsSystems/gitbook-distributor-guide/pull/36/files)

## 18.06.2020

* Removed `AlwaysIncluded` field from [Product](./operations.md#product) \([37](https://github.com/MewsSystems/gitbook-distributor-guide/pull/37/files)\). In order to pre-select a product during a booking, you can use `IncludedByDefault` field.

## 22.04.2020

* Added following sections: Configuration, Theme, City, PaymentCardInput, RequiredField, Enterprise and Address.

## 18.03.2020

* Added `close()` FE api description.

## 04.03.2020

* Added SendMarketingEmail field to Booker.

## 03.03.2020

* Added enums for RateGroups section and some minor improvements.

## 26.02.2020

* Added documentation for `hotels/getPaymentConfiguration`.
* Deleted old/legacy `payments/getPaymentGateway`.

