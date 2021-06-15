# Distributor Standalone

Distributor for your hotel is available as standalone version, hosted on our servers. You can simply provide a link from your website and not worry about anything else.

Address of the Distributor standalone page has the following format:

```text
https://www.mews.li/distributor/aaaa-bbbb-cccc-dddd-eeeeeeee
```

The `aaaa-bbbb-cccc-dddd-eeeeeeee` part should be replaced with your Distributor configuration id. See [Where to get configuration id](./faq.md#where-to-get-configuration-id) for details about where to find.

⚠️ Make sure you are using Distributor configuration id, not enterprise id or other id.

## Multi-enterprise Distributor

If you want to use a Distributor with multiple enterprises, you can place several Distributor configurations ids together separated by a semicolon. \(The theme will be pulled from the id of the first configuration in the URL\).

```text
https://www.mews.li/distributor/aaaa-bbbb-cccc-dddd-eeeeeeee;ffff-gggg-hhhh-iiii-jjjjjjjj
```
