# Distributor Widget with a date picker

This guide will show you how to create a date form which will open Distributor with given dates after users submit it. 

Here you can see the final result of what you'll be creating:
https://codepen.io/zdrazil/pen/PojeMYY

## Prerequisites
- You have followed [Getting started guide](../getting-started.md) and understand how Distributor Widget is installed.
- Some familiarity with JavaScript and HTML.

## Install Distributor loader script

Place the following `<script>` code snippet as is in the `<head>` of your web page's HTML output, preferably as close to the opening `<head>` tag as possible.

```html
<script src="https://www.mews.li/distributor/distributor.min.js"></script>
```

For more details see [getting started section for installing Distributor loader script](../getting-started.md#install-distributor-loader-script)

## Add the date form

Place this code for date form somewhere in the `body` of your HTML page.

```html
<form id="date-form" type="submit">
  <label for="start">Start date:</label>
  <input type="date" id="start" name="trip-start" required>
  <label for="end">End date:</label>
  <input type="date" id="end" name="trip-end" required>
  <input type="submit" id="submit" value="Submit">
</form>
```

The submit button in the form is disabled for now, so users can't submit the form until the form and Distributor Widget are ready to be used. We will add the code to enable it in later steps.

## Initialize Distributor Widget 

Place the initialization code inside a `script` tag just before the closing `</body>` tag.

```html
<script>
  Mews.Distributor({
      // 1.
      "configurationIds": ["Your Distributor configuration id"]
    },
    // 2.
    function(distributor) {
    },
  );
</script>
```

### Comments
1. Sets the configuration id for your Distributor. If you are not sure where to find it, see [getting started secion for initializing Distributor Widget](../getting-started.md#initialize-distributor-widget) for details.
2. Sets callback to be used when Distributor finishes loading/initialzing. Right now it's not doing anything. We will extend it in the next section.

## Decide which environment the Distributor Widget should use

{% hint style="warning" %}
By default Distributor Widget uses production environment and data. If this is what you want, you should skip this section.
{% endhint %}

But if you want to use Distributor Widget with demo data, you need set [dataBaseUrl](../reference.md#string-databaseurl.md) with this code:

```html
<script>
  Mews.Distributor({
      "configurationids": ["your Distributor configuration id"]
    },
    function(distributor) {
    },
    { databaseurl: 'https://api.mews-demo.com' }
  );
</script>
```

Examples in later sections of this guide assume you want to use production environment and omit `dataBaseUrl` option.

## Add callback to enable Submit button and open Distributor Widget

Your callback, which is called when Distributor is ready to be used, needs to do 2 things:
1. Listen on the submit button and when users submit it, open Distributor with the given dates.
2. Enable the Submit button when Distributor Widget is ready to be used.

This code will do both:
```html
<script>
  Mews.Distributor({
      "configurationIds": ["e31209f1-8be9-49d0-a577-ab73009151f3"]
    },
    function(distributor) {
      // 1.Listen on submit and when users submit, open Distributor with given dates.
      const listenOnSubmit = () => {
        // Find the form in DOM and listen on submit.
        const form = document.getElementById("date-form");
        form.addEventListener("submit", (event) => {
          // Don't use the default submit button behavior. We want to handle it ourselves.
          event.preventDefault();
          // Get the dates from the date form.
          const {
            start,
            end
          } = event.target.elements;
          const startDate = new Date(start.value);
          const endDate = new Date(end.value);
          // Use Distributor Widget API to set the dates in Distributor Widget and open it.
          distributor.setStartDate(startDate);
          distributor.setEndDate(endDate);
          distributor.open();
        });
      };
      listenOnSubmit();
      // 2. Enable the submit button, because Distributor Widget is ready to be used.
      const enableSubmit = () => {
        const submitButton = document.getElementById("dates-submit");
        submitButton.value = "Submit";
        submitButton.disabled = false;
      };
      enableSubmit();
    },
  );
</script>
```

After you add this code you have a form which upon submit opens Distributor Widget with given dates.

You can see the final result here: https://codepen.io/zdrazil/pen/PojeMYY

## Conclusion

In this article, you've learned how to add a simple date form to your page and connect its submit button to Distributor Widget. So when users select the dates and submit it, Distributor Widget will open with given dates.

Distributor Widget API supports more than setting dates and opening it. See the other [Distributor Widget API options](../reference.md) to find other interesting options you could use.
