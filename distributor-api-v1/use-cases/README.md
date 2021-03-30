# Distributor API Use cases

This section describes, how to use the Distributor API in order to implement well-known scenarios.
The following types scenarios can be achieved:

## On session payments
Whenever a user create reservation there is an option to allow him pay directly. This needs to be correctly configured via
settlement rules on `RateGroup`. We provide this functionality only for `Rates` where the payment is taken immediately when
the reservation is created. In order to simplify the workflow we offer this functionality in our payment gateway via a feature
called "Payment request". [Read more](./on-session-payments.md) about on session payments how to implement this behavior.
