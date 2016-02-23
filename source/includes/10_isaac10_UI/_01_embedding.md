## Embedding and Initialization

> Embedding and Initialization

```html
<script type="text/javascript" src="https://app.isaac10.com/api/v1/isaac10_api.js"></script>
<script type="text/javascript" src="https://app.isaac10.com/ui/isaac10_ui.js"></script>

<script type="text/javascript">
  // Initialization of JavaScript API
  var isaac10 = new Isaac10("your-subdomain");

  // Initialization of isaac10 UI
  isaac10UI.setup({
    "isaac10Instance": isaac10,
    "fetchTemplate":  "bootstrap3",
    "locale":         "de"
  }).render("#isaac10-ui");
</script>
```

> Rendering

```html
<div id="isaac10-ui"></div>
```

To be able to use the _isaac10 UI_, the JavaScript library of _isaac10_ must be loaded as well.
See right side, for how to initialize the _isaac10 UI_ and render it on your website.

### Configuration

Parameter | Description | Possible Values
----------|-------------|----------------
**isaac10Instance** | | An instance of the `Isaac10` object.
**fetchTemplate** | the HTML templates (or handlebar templates) to be loaded | <ul><li>`false` (no templates will be loaded, you have to provide the templates yourself)</li><li>`"bootstrap3"`</li></ul>
**overrideTranslations** | See [Overwriting and Adding Translations](#overwriting-and-adding-translations) | A JavaScript object, structured like a translation file.
**locale** | The language that should be used in the _isaac10 UI_ | <ul><li> `"de"` (german)</li><li>`"en"` (english)</li></ul> More languages can be added through the **overrideTranslations** parameter.

### Display the isaac10-UI

The call of `.render()` rendered the _isaac10 UI_ in the HTML element, referenced by the passed jQuery selector (as shown in the given example: the element with ID `#isaac10-ui`). The element should be a `<div>` tag but can be anything else.

### Navigating through the isaac10-UI

The page to be displayed is controlled by an URL anchor. If the _isaac10 UI_ is rendered on a page with an URL without anchor, only a test page will be displayed, stating: **isaac10-UI works!**

The following pages are available:

-   the [Registration Page for new Customers](#registration-page-for-new-customers)
-   Overview and forms for account data
-   bills overview
-   subscriptions overview and forms to have the subscriptions managed

More pages can be reached by clicking on the links on these pages.
