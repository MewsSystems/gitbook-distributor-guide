# Distributor Standalone

Distributor for your hotel is available as standalone version, hosted on our servers. You can simply provide a link from your website and not worry about anything else.

Address of the Distributor standalone page has the following format:

```text
https://www.mews.li/distributor/aaaa-bbbb-cccc-dddd-eeeeeeee
```

The`aaaa-bbbb-cccc-dddd-eeeeeeee`part should be replaced with id of your Distributor configuration. You can also use the Enterprise ID \(this will use the hotels default distributor configuration set up\). In case of multiple hotel configuration, you are NOT able to use a mixture of Distributor configuration ID and Enterprise ID.

## Chain Distributor <a id="chain-distributor"></a>

If you want to use a chain distributor with multiple properties, you can place several Distributor configurations identifiers/Hotel identifiers together separated by a semicolon. \(The theme will be pulled from the I.D. of the first hotel in the URL\)

```text
https://www.mews.li/distributor/aaaa-bbbb-cccc-dddd-eeeeeeee;ffff-gggg-hhhh-iiii-jjjjjjjj
```

