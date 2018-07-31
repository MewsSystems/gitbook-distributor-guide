# Distributor Widget

## Script {#script}

Include the following Distributor loader script into your website:

```javascript
<script src="https://www.mews.li/distributor/distributor.min.js"></script>
```

The script should be included in the`<head>`section \(do not attach the`async`attribute\). The script size is kept as minimal as possible \(cca 11 kB gzipped\) to allow quick webpage initialization. The widget script is then downloaded asynchronously and inserted automatically into your website afterwards.

Please note that serving the script from our CDN servers ensures seamless releases of new features, bugfixes and improvements. Therefore, we discourage you from packing the contents of this script into your own JavaScript bundle. Make sure to follow the recommended way of including the scripts via`<script>`HTML tag.

## Usage {#usage}

Once the Distributor loader script is processed by the browser, you can initialize the Distributor widget with the following code.

**Important:** The initialization needs to be called only after the website is loaded, to ensure everything is ready. The easiest way to achieve this is to place it just before the closing`</body>`tag.

This creates a isolated \(iframe based\) overlay on your website and loads Distributor into it.

```javascript
<!-- Distributor's initialization call, creating new instance of Distributor. Use id of your Distributor configuration. -->
<script>
Mews.Distributor({
    configurationIds: [
        'Your Distributor configuration id'
    ],
    openElements: '.distributor-open'
});
</script>
```

Do not forget to**replace the placeholder** `Your Distributor configuration id` **with a real Distributor configuration id**. You can get your Distributor configuration id from the configuration’s detail page in Mews Commander. The id is shown there as Identifier in format`aaaa-bbbb-cccc-dddd-eeeeeeee`.

The overlay is not visible by default - to actually display it, you should bind its opening to some action \(i.e. clicking on a button\). Distributor can do it automatically for you, if you provide the second option`openElements`- a string of comma-separated CSS selectors of elements, whose click events will be binded with opening of Distributor. The event is delegated, so you can pass selectors to elements that don’t exist during the load of website. You can get more info on how the selectors can look like [here](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll) for example.

```javascript
<!-- Example of button for opening the Distributor when openElements is set to '.distributor-open' -->
<button class="distributor-open">Book Now</button>
```

### Advanced usage {#advanced-usage}

If you need a more specific setup for opening Distributor, or you want to call some API functions on a Distributor instance, you can provide a callback function as the second argument to the initialization call - the instance is provided as an argument to the callback.

Very common example for this is using a custom start and end date selectors that are part of your website and then passing user’s selection to Distributor.

```javascript
<!-- Example of setting custom dates. Useful if you have i.e. own calendars on website. -->
<script>
Mews.Distributor({
    configurationIds: [
        'Your Distributor configuration id'
    ]
},
function (distributor) {
    // you can call API functions on a distributor instance here
    // set different start and end date
    distributor.setStartDate(new Date(2018, 1, 1));
    distributor.setEndDate(new Date(2018, 1, 3));
});
</script>
```

To see a list of all available API calls, please consult [API ](reference.md#api-reference)section.

Closing of Distributor is provided in the overlay by default, so you don’t have to worry about that.

### Chain Distributor {#chain-distributor}

Distributor can run in two basic modes - for a _Single_ property or for a _Chain_. The mode is chosen automatically during initialization, based on the count of hotel ids you have provided in the options. Whenever two or more hotels are loaded, the Distributor will start in the _Chain_ mode. That means that it will add one more step to the booking flow - hotel selection. To add more hotels, simply pass ids of their configurations into the`configurationIds`array option:

```javascript
<script>
Mews.Distributor({
    configurationIds: [
        'First configuration id',
        'Second configuration id',
        // and more...
    ]
});
</script>
```

## Styles {#styles}

Distributor does not use separate CSS files, everything is packed inside the script. For possible customizations, consult [Customization](reference.md) section.

## Done! {#done}

This is all you need for the basic setup of Mews Distributor.

