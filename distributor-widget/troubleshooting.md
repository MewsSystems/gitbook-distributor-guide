# Troubleshooting Distributor Widget 

## Distributor shows an error "mews.li refused to connect", browser says it can't open page because of security or there's a console error mentioning mews.li and X-Frame-Options

![mews.li refused error Google Chrome](../.gitbook/assets/mews-li-refused-connect-chrome.png)
![mews.li refused error Mozilla Firefox](../.gitbook/assets/mews-li-refused-connect-firefox.png)

- `[Error] Refused to display 'https://www.mews.li/Distributor' in a frame because it set 'X-Frame-Options' to 'sameorigin'.`
- `The loading of "https://www.mews.li/Distributor" in a frame is denied by "X-Frame-Options" directive set to "sameorigin".`

Distributor is not working because Distributor is not installed correctly on your page. Installing Distributor in other way than as guides describe is not supported and can cause errors such as "mews.li refused to connect".

You can try to confirm Distributor is not installed correctly by inspecting the DOM of the page:
- Open page with Distributor and make it show the error.
- Open your browser developer tools with DOM/elements inspector.
- In the inspector look for any tags like `<iframe src="https://www.mews.li/distributor/aaaa-bbbb-ccc-ddd">`.

There shouldn't be any iframe tag with a `src` attribute pointing to `mews.li` domain.

If you find something like that, the problem could be in the way the Distributor is installed. And even if you didn't find anything like that, it's better to check if Distributor is installed correctly.

### How to fix it

[Decide if what you want to use/are using is Distributor Standalone or Distributor Widget](../README.md).

Go through relevant installation guide and make sure your page and code is doing everything correctly:
- [Distributor Standalone Getting started guide](../distributor-standalone/getting-started.md)
- [Distributor Widget Getting started guide](./getting-started.md)

If you are using [Distributor Widget](./README.md), pay special attention to [the requirements section of the Distributor Widget Getting started guide](./getting-started.md#requirements). It has a list of things to do and don't do during the installation of Distributor.
