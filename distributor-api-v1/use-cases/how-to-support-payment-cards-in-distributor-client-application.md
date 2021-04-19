# How to support payment cards in Distributor client application

When creating a reservation it is possible to attach a payment card to the reservation.

As part of creating your own custom Distributor client you may want to have a form within your client application where customers
can enter their payment card data and send this data to Distributor API for further use. Payment card data can then
be used by Mews in for charging the customer.

To do that Distributor some API endpoints can support or require [CreditCardData](../operations.md#creditcarddata)
in the request.

### Where to get `CreditCardData` values

* Confirm that **property supports PCI Proxy** by checking the field [PaymentCardStorageType](../operations.md#paymentcardstoragetype) in Distributor API response. Also read docs about [PaymentGateway](operations.md#payment-gateway) to see what other API data you could potentially use for your implementation.
* Use [PublicKey](operations.md#payment-gateway) as `merchantId` while implementing PCI Proxy fields. Follow PCI Proxy [guide](https://docs.pci-proxy.com/collect-and-store-cards/capture-iframes) to handle the sensitive card data and obtain `PaymentGatewayData`.
  * PCI Proxy documentation only highlights the sandbox endpoints (used for staging environment). In production environment, you have to omit the `sandbox.` part from the address. For example `https://pay.sandbox.datatrans.com/upp/payment/js/secure-fields-2.0.0.min.js` then becomes `https://pay.datatrans.com/upp/payment/js/secure-fields-2.0.0.min.js` .
* PCI Proxy service will return you a `transactionId` in the response which will be used as `PaymentGatewayData` inside [CreditCardData](operations.md#creditcarddata).
* Rest of the [CreditCardData](../operations.md#creditcarddata) fields can be passed in a plain text because those are not considered sensitive from PCI DSS points of view.

