# On session payments

Whenever a user create reservation there is an option to allow him pay directly. This needs to be correctly configured via
settlement rules on `RateGroup`. We provide this functionality only for `Rates` where the payment should be automatically
taken immediately when the reservation group is created. In order to simplify the workflow we offer this functionality
in our payment gateway via a feature called "Payment request".

## Creating a reservation group

First step of the entire workflow is to [create a reservation group via our API](../operations.md#request-apibaseurlapidistributorv1reservationgroupscreate).
The response contains a new field `PaymentRequestId` which we will use later on for a redirect to a payment gateway.
The payment gateway does support an optional query parameter `returnUrl` which will be used to return the user into
your booking engine after successful payment or in case the user decide to abandon the flow. `returnUrl` value should
be a Base64 encoded absolute url e.g. `btoa(https://www.domain.tld/)`. After the user returns to your
booking engine you can verify the state of the payment request by calling [get reservation group API](../operations.md#get-reservation-group)
with `Extent` for `PaymentRequests` and optionally for `Payments` where you want to validate.
Once the [Payment request State](../operations.md#payment-request-state) and optionally [Payment State](../operations.md#payment-state).

## Step by step workflow
1) [Create new reservation group](../operations.md#request-apibaseurlapidistributorv1reservationgroupscreate)
2) Get `PaymentRequestId` from the response
3) Create a `ReturnUrl` via encoding your url by `base64` e.g. `btoa('https://www.domain.tld/booking/completed/[ReservationGroupId]')`
4) Redirect the user to the gateway on url `https://[MewsApplicationsBaseUrl]/navigator/payment-requests/detail/[PaymentRequestId]?returnUrl=[ReturnUrl]`
5) After the user returns to the `ReturnUrl` in your booking engine you can verify the state by [reservation group detail](../operations.md#request-apibaseurlapidistributorv1reservationgroupsget) with a specified [Extent](../operations.md#reservation-group-get-extent)
6) Validate the state of the Payment request in the response

{% hint style="info" %}
Till the Payment request enter its [finite state](../operations.md#payment-request-state) you can redirect the user again e.g. with "Try to pay again" button.
In case the Payment request expires or is canceled automatic settlement will take care of the payment, and it will try to charge the settlement amount as soon as possible.
{% endhint %}
