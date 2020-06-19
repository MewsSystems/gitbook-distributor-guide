# Changelog

## 18.06.2020

* Removed `AlwaysIncluded` field from [Product](operations.md#product) ([37](https://github.com/MewsSystems/gitbook-distributor-guide/pull/37/files)). This flag does not have any meaning anymore. The API is returning its value always equal to `false`. In order to pre-select a product during a booking, you can use `IncludedByDefault` flag.

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