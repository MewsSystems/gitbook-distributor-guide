# Changelog

## 20/07/2018 {#12072017}

* Corrected error in documentation for `distributorReservationCreated` event - There shouldn't be `reservation` prefix in data layer variable names \(i.e. use just `startDate` instead of `reservation.startDate`\).

## 12/07/2017 {#12072017}

* Added direct use of GA Linker plugin during redirect to Mews Merchant.
* Added`distributorConfigurationSet`event with the initial data set.

## 14/06/2017 {#14062017}

* Fixed prices localization bug.

## 01/06/2017 {#01062017}

* Fixed GTM tracking initialization after redirect to Merchant.

## 26/05/2017 {#26052017}

* Hotfix of the GTM tracking bug.

## 24/05/2017 {#24052017}

* Fixed initialisation of the GTM container. It now won’t trigger any event until the Distributor is opened for the first time.

