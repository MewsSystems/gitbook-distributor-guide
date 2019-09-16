# Advanced Guide

## Full example

> **Note:**
>
> Direct configuration of Distributor through the options has been deprecated and it will be disabled in future. Prefer to use Distributor Configuration in Commander. The only supported now are`configurationIds`and`openElements`.

Example with all possible options and their default values follows. To get further information about the options and an API call, see the [reference](reference.md).

**Important: This is just an example, do not copy this directly to your website!**

```javascript
<script>
Mews.Distributor({
    // required
    configurationIds: [
        'aaaa-bbbb-cccc-dddd-eeeeeeee'
    ],
    // optionals
    openElements: '',
},
function(distributor) {
    // Always available api calls
    // distributor.open();
    // distributor.setLanguageCode(languageCode);
    // distributor.setCurrencyCode(currencyCode);
    // distributor.setStartDate(date);
    // distributor.setEndDate(date);
    // distributor.setVoucherCode(code);
    // distributor.setRooms(rooms);
    // Singlehotel mode api calls
    // distributor.showRooms();
    // distributor.showRates(roomId);
    // Multihotel mode api calls
    // distributor.showHotels();
    // distributor.showRooms(hotelId);
    // distributor.setCity(cityId);
});
</script>
```

#### Note  <a id="note-1"></a>

See that you have just one`<script>`tag containing`Mews.Distributor`call on your page.

### Deeplinks  <a id="deeplinks"></a>

Distributor recognises a set of parameteres passed to it in a URL query. This allows you to deeplink into booking engine from other websites. **Important: This should not be used as a standard way to open Distributor from your own website**

Recognised parameters are:

| Name | Description |
| :--- | :--- |
| mewsDistributorOpened | tells the Distributor to open automatically |
| mewsStart | an arrival date in ISO 8601 format \(`YYYY-MM-DD`\) |
| mewsEnd | a departure date in ISO 8601 format \(`YYYY-MM-DD`\) |
| mewsVoucherCode | a voucher code |
| mewsRoute | opens on specified step \(one of `rooms`, `rates`\) |
| mewsRoom | opens with specified room selected \(`aaaa-bbbb-cccc-dddd`\) |
| language | a language code \(`xx-YY`\) |
| currency | a currency code \(`XXX`\) |

In addition, Distributor in multihotel mode also recoqnize:

| Name | Description |
| :--- | :--- |
| mewsCityId | opens with specified city selected \(`aaaa-bbbb-cccc-dddd`\) |
| mewsHotel | opens with specified hotel selected \(`aaaa-bbbb-cccc-dddd`\) |
| mewsRoute | in addition to `rooms` and `rates`, supports also `hotels` step |

#### Examples  <a id="examples"></a>

* presets a start date, voucher code and language, but Distributor stays closed

  ```text
  http://www.yourwebsite.com/?mewsStart=2015-01-01&mewsVoucherCode=special-discount&language=en-US
  ```

* opens Distributor with preselected room and currency on rate selection step

  ```text
  http://www.yourwebsite.com/?mewsDistributorOpened&currency=EUR&mewsRoute=rates&mewsRoom=aaaa-bbbb-cccc-dddd
  ```

* opens multihotel Distributor with preselected city hotel selection step

  ```text
  http://www.yourwebsite.com/?mewsDistributorOpened&mewsRoute=hotels&mewsCityId=aaaa-bbbb-cccc-dddd
  ```

#### Note  <a id="note-2"></a>

The deeplinks are also supported by standalone Distributor.

### Payment Gateways  <a id="payment-gateways"></a>

Payment gateway is used to safely collect information about a customer’s credit card. A configuration is done once, when the hotel is set up. Distributor would use it automatically. Currently Distributor supports these gateways:

* [Braintree](https://www.braintreepayments.com/)
* [Adyen](https://www.adyen.com/home)
* Mews Merchant

Using payment gateway is not mandatory, as reservations can be created without providing a credit card information.

**Important:** PCI Security Standard requires you to use **SSL Certificate** on your website to be allowed to collect any payments info. This happens when using Braintree or Adyen gateways.

#### Mews Merchant  <a id="mews-merchant"></a>

When using the Mews Merchant gateway integration in Distributor on your website, a customer will be redirected to a mirroring Distributor hosted at [https://wwww.mews.li/](https://wwww.mews.li/) just before entering their payment details. This is a requirement when using Mews Merchant. When closing the Distributor, the customer will be redirected back to your website

