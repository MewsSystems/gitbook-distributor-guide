# Payment Gateway Data

`PaymentGatewayData` is an encoded representation of card number and CVV which is used to provide payment card data to Distributor API.

You can use a combination of [PCI Proxy client side encryption library](https://docs.pci-proxy.com/collect-and-store-cards/capture-iframes) and your own custom implementation of Distributor client to obtain in.

You can then use it to [add payment cards support to custom Distributor client](general-guidelines.md#howtosupportpaymentcardsincustomdistributorclient).
