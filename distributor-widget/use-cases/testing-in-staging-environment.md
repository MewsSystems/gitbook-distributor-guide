# Testing Distributor Widget in demo/staging/testing environment

Distributor Widget uses production environment by default.

Before you are ready to run Distributor Widget against real data, you can use Distributor Widget with [staging/testing environment](../../distributor-api-v1/environments.md) data instead.

Most of the steps are the same as in [Getting started section](../getting-started.md).

The only difference is in the [initialization of the Distributor Widget](../getting-started.md#initialize-distributor-widget).

In comparison to the default example, you can set an [optional `dataBaseUrl`](../reference.md#string-databaseurl) property to the testing/staging API URL:

```javascript
Mews.Distributor(
    { configurationIds: ['aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee'] },
    function (api) { api.open(); },
    { dataBaseUrl: 'https://api.mews-demo.com' }
);
```

Make sure you use configurationIds from the correct environment. Otherwise, the configurationIds [won't be used](../../faq.md#why-distributor-doesnt-use-the-configuration-ids-ive-provided).

After doing this, Distributor Widget will start using the data from [staging/testing environment](../../distributor-api-v1/environments.md), instead of from the production.
