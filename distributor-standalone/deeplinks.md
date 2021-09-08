# Deeplinks

With deeplinks you can create URLs which, when used, open Distributor standalone in some predefined setup. For example with a specific currency or dates. 

You can deeplink into a standalone Distributor from other websites by passing [supported parameters](./deeplinks.md#supported-parameters) in a URL query. For example like this:

```text
https://www.mews.li/distributor/aaaa-bbbb-cccc-dddd-eeeeeeee?currency=EUR&mewsRoute=rates&mewsRoom=aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee
```

## Supported parameters 

Parameters can be combined and some have no visible effect unless they are used in combination (e.g. `mewsHotel`).

### Parameters supported in single and multi-enterprise mode

| Name | Description | Example |
| :--- | :--- | :--- |
| mewsStart | an arrival date in ISO 8601 format \(`YYYY-MM-DD`\) | `2023-01-20` for January 20, 2023 |
| mewsEnd | a departure date in ISO 8601 format \(`YYYY-MM-DD`\) | `2023-01-23` for January 23, 2023 |
| mewsVoucherCode | a voucher code | `E1A71167851A30043B12` |
| mewsRoute | [mewsRoute](./deeplinks.md#parameter-mewsRoute) | `rooms` for rooms step |
| mewsRoom | opens with specified room selected \(`aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee`\) | `da394bbb-9685-4bb8-9547-ab7300915967` |
| language | a language code \(`xx-YY`\) | `en-US` for U.S. English |
| currency | a currency code \(`XXX`\) | `USD` for United States dollar |

### Additional parameters supported in multi-enterprise mode

In addition, Distributor in multi-enterprise mode also supports:

| Name | Description | Example |
| :--- | :--- | :--- |
| mewsCityId | selects specified city \(`aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee`\) | `cf1678c0-0896-450b-8611-bec07d63cc32` |
| mewsHotel | selects specified hotel \(`aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee`\) | `e31209f1-8be9-49d0-a577-ab73009151f3` |

### Parameter mewsRoute

With parameter `mewsRoute` you can open Distributor on a specific step.

{% hint style="warning" %}
Available steps differ based on if you use single or multi-enterprise Distributor. Some steps also require additional parameters to be set, otherwise mewsRoute parameter will not work correctly. See following [table](./deeplinks.md#mewsroute-parameter-in-single-enterprise-mode) for details.
{% endhint %}

#### mewsRoute parameter in single-enterprise mode

| Step | Required parameters |
| :--- | :--- |
| `mewsRoute=rooms` | none |
| `mewsRoute=rates` | mewsRoom |

#### mewsRoute parameter in multi-enterprise mode

| Step | Required parameters |
| :--- | :--- |
| `mewsRoute=hotels` | mewsCityId |
| `mewsRoute=rooms` | mewsCityId, mewsHotel |
| `mewsRoute=rates` | mewsCityId, mewsHotel, mewsRoom |

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
