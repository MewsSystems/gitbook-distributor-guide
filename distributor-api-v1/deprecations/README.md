# Deprecations

This page contains a list of past and future deprecations in the API. Deprecation information are present in individual pages. `Deprecation notice` is a date from which we do support both versions (previous/deprecated and next/living standard). `Removal date` is a date where we aim to remove the previous/deprecated variant of the API.

| Deprecation | Object | Property | Replaced by | Deprecation notice | Removal date |
|:------------|:------------|:-------------------|:-------------|:-------------|:-------------|
| [Average amount per night](./average-amount-per-night.md) | [Room price](../operations.md#room-price) | `AverageAmountPerNight` | `AverageAmountPerTimeUnit` | 21.7.2021 | 31.11.2021 |
| [Maximum nights for settlement](./settlement-maximum-nights.md) | [Rate group](../operations.md#rate-group) | `SettlementMaximumNights` | `SettlementMaximumTimeUnits` | 21.7.2021 | 31.11.2021 |
| [Product charging](./product-charging.md) | [Product](../operations.md#product) | `Charging` | `ChargingMode` | 21.7.2021 | 31.11.2021 |
| [Product posting](./product-posting.md) | [Product](../operations.md#product) | `Posting` | `PostingMode` | 21.7.2021 | 31.11.2021 |
| [Product pricing](./product-pricing.md) | [Product](../operations.md#product) | `Amounts` & `RelativePrice` | `Pricing` | 1.7.2021 | 31.11.2021 |
| [Payment card input](./payment-card-input.md) | [Configuration](../operations.md#configuration) | `PaymentCardInput` | `PaymentCardRequirement` | 18.4.2021 | 31.7.2021 |
