# Getting started

{% hint style="info" %}
In order to embed the Distributor into your webpage, your site must be securely served over HTTPS.

Any Distributor widget that is implemented on an insecure HTTP site will be redirected to the [standalone Distributor](../distributor-standalone.md).
{% endhint %}

By using Distributor Widget your users can book directly from your website.

At a high level, the steps to start using Distributor Widget are:
* [Install Distributor loader script](./README.md#install-distributor-loader-script).
* [Initialize Distributor Widget](./README.md#initialize-distributor-widget) through a global `Mews.Distributor` object that the loader script exposes.
* [Setup opening of Distributor Widget overlay](./README.md#setup-overlay-opening).
* Optional: Use callback function to [control Distributor Widget](./README.md#optional-control-distributor-widget).
* Optional: Know the difference between [single and multi-enterprise Distributor](./README.md#multi-enterprise-distributor) and set it up.

## Install Distributor loader script

To use Distributor Widget, you need to install Distributor loader script with a code snippet provided in the [Installation](./README.md#installation) section.

The script will asynchronously prepare global `Mews.Distributor` object which you're going to use in further steps to initialize Distributor Widget.

### Requirements

You need to use the code snippet as is and as described. Doing otherwise will cause unexpected problems and is not supported.

* Do not place it anywhere else than in the `<head>`.
* Do not modify it in any way and do not attach the `async` attribute.
* Do not pack the contents of the script files that the code snippet references into your own JavaScript bundle.
* If you have a Content Security Policy (CSP) setup on your website, you need to [enable the domains Distributor uses](./README.md#content-security-policy).

The script file size is kept as minimal as possible (approx 11 kB gzipped) to allow quick webpage initialization. Also, serving the script from our CDN servers ensures seamless releases of new features, bugfixes and improvements.

### Installation

Place the following `<script>` code snippet as is in the `<head>` of your web page's HTML output, preferably as close to the opening `<head>` tag as possible.

```html
<script src="https://www.mews.li/distributor/distributor.min.js"></script>
```

#### Content Security Policy

If you have a Content Security Policy (CSP) setup on your website, the following domains should be enabled for Distributor to function correctly.

```text
mews.li
*.mews.li
https://pay.datatrans.com/upp/payment/js/secure-fields-1.0.0.js
```

The last, datatrans, URL is for [PCI Proxy](https://www.pci-proxy.com/) which is the secure, PCI-DSS complaint solution that is used by our Merchant to process payment cards.

## Initialize Distributor Widget

After the website has loaded, and the Distributor loader script prepared the global `Mews.Distributor` object, you can initialize Distributor Widget by calling global `Mews.Distributor` with some arguments:

{% hint style="info" %}
**Important:** Make sure you initialize Distributor Widget by calling `Mews.Distributor` **only after** the website is loaded, otherwise the initialization will fail or not complete fully. 

The easiest way to achieve this is to place the initialization code inside a `script` tag just before the closing `</body>` tag. But you can use a different approach, if you want.
{% endhint %}

In the following snippet, **replace the placeholder** `Your Distributor configuration id` with a **real Distributor configuration id** from the correct [environment](../distributor-api-v1/environments.md). Here's more info about [where to get the configuration id](../faq.md#where-to-get-configuration-id).

```html
<!-- Distributor's initialization call, it creates new instance of Distributor. Use your Distributor configuration id. -->
<script>
Mews.Distributor({
    configurationIds: [
        'Your Distributor configuration id'
    ],
    openElements: '.distributor-open'
});
</script>
```

This call creates an isolated (iframe based) overlay on your website and loads Distributor into it.

{% hint style="warning" %}
The overlay and Distributor is not visible by default. You're going to solve this in the next section.
{% endhint %}

## Setup overlay opening

To display the Distributor overlay, you should bind its opening to some action (e.g. clicking on a button).

Distributor can set this binding automatically for you, if you provide the second option `openElements` to `Mews.Distributor` and prepare the HTML elements which will be binded. You can find more info about `openElements` in [Options reference](./reference.md#options-reference).

The binding is delegated, so the elements and selectors don't need to exist during load of the website, but you still need to add the HTML elements yourself.

Knowing that, you can for example add the following HTML button with class `distributor-open` (the class name we've used in the initialization code in code snippet from the previous section), and it  will open the Distributor Widget overlay upon a click:

```html
<!-- Example of button for opening the Distributor when openElements is set to '.distributor-open' -->
<button class="distributor-open">Book Now</button>
```

It's just an example, the automatic binding can attach click event listener to any HTML element.

{% hint style="info" %}
Closing of Distributor is provided in the overlay by default, no configuration needed from your side.
{% endhint %}

## Done!

This is all you need for the basic setup of Mews Distributor.

### What you've done:
- On page with this setup, loader script will prepare `Mews.Distributor`.
- After the page loads, your code will call `Mews.Distributor`. This will initialize Distributor Widget, create (for now) hidden overlay and bind opening actions to selected HTML elements, like buttons.
- When users click these HTML elements, Distributor Widget overlay will open, and they can book through it.
- They can close it anytime and see your page again.

## Optional: Control Distributor Widget

If you want to have a more customized setup, or you want to call some API functions on a Distributor instance to control it, you can provide a callback function as the second argument to the initialization call. 

This callback is later called asynchronously with an argument - Distributor instance. By calling methods on this instance you can control Distributor.

Very common example of this is using a custom start and end date selectors that are part of your website and then passing user’s selection to Distributor.

```html
<!-- Example of setting custom dates. Useful if you have i.e. own calendars on website. -->
<script>
Mews.Distributor(
    {
        configurationIds: [
            'Your Distributor configuration id'
        ],
        openElements: '.distributor-open'
    },
    function (distributor) {
        // you can call API functions on a distributor instance here
        // set different start and end date
        distributor.setStartDate(new Date(2018, 1, 1));
        distributor.setEndDate(new Date(2018, 1, 3));
    }
);
</script>
```

{% hint style="info" %}
To see a list of all available API calls, please consult [Widget API reference](./reference.md#api-reference).
{% endhint %}

### Multi-enterprise Distributor

Distributor can run in two basic modes - for a single enterprise or for multiple. The mode is chosen automatically during initialization, based on the count of configuration ids you have provided in the options. Whenever two or more hotels are loaded, the Distributor will start in the multi-enterprise mode. That means that it will add one more step to the booking flow - hotel selection. To add more hotels, simply pass their configuration ids into the`configurationIds`array option (here's [how you can get the configuration ids](../faq.md#where-to-get-configuration-id)):

```html
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
