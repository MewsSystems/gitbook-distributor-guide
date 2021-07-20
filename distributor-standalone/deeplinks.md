# Deeplinks

With deeplinks you can create links which, when used, open Distributor standalone in some predefined setup. For example with a specific currency or dates. 

You can deeplink into standalone Distributor from other websites by passing [supported parameters](./deeplinks.md#supported-parameters) in a URL query. 

Like this:
```text
https://www.mews.li/distributor/aaaa-bbbb-cccc-dddd-eeeeeeee?currency=EUR&mewsRoute=rates&mewsRoom=aaaa-bbbb-cccc-dddd
```

## Supported parameters 

These parameters can be combined.

| Name | Description |
| :--- | :--- |
| mewsStart | an arrival date in ISO 8601 format \(`YYYY-MM-DD`\) |
| mewsEnd | a departure date in ISO 8601 format \(`YYYY-MM-DD`\) |
| mewsVoucherCode | a voucher code |
| mewsRoute | opens on specified step \(one of `rooms`, `rates`\) |
| mewsRoom | opens with specified room selected \(`aaaa-bbbb-cccc-dddd`\) |
| language | a language code \(`xx-YY`\) |
| currency | a currency code \(`XXX`\) |

### Additional parameters supported in multi-enterprise mode

In addition, Distributor in multi-enterprise mode also supports:

| Name | Description |
| :--- | :--- |
| mewsCityId | opens with specified city selected \(`aaaa-bbbb-cccc-dddd`\) |
| mewsHotel | opens with specified hotel selected \(`aaaa-bbbb-cccc-dddd`\) |
| mewsRoute | in addition to `rooms` and `rates`, supports also `hotels` step |

## Examples

## Open with specific start date, voucher code and language

```text
https://www.mews.li/distributor/aaaa-bbbb-cccc-dddd-eeeeeeee?mewsStart=2021-01-01&mewsVoucherCode=special-discount&language=en-US
```

## Open with preselected room and currency on rate selection step

```text
https://www.mews.li/distributor/aaaa-bbbb-cccc-dddd-eeeeeeee?currency=EUR&mewsRoute=rates&mewsRoom=aaaa-bbbb-cccc-dddd
```

## Opens multi-enterprise Distributor with preselected city hotel selection step

```text
https://www.mews.li/distributor/aaaa-bbbb-cccc-dddd-eeeeeeee?mewsRoute=hotels&mewsCityId=aaaa-bbbb-cccc-dddd
```
