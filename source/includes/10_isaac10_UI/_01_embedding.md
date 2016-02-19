## Embedding and Initialization

> Embedding and Initialization

```html
<script type="text/javascript" src="https://app.isaac10.com/api/v1/isaac10_api.js"></script>
<script type="text/javascript" src="https://app.isaac10.com/ui/isaac10_ui.js"></script>
```

```javascript
// Initialization of JavaScript API
var isaac10 = new Isaac10("your-subdomain");

// Initialization of isaac10 UI
isaac10UI.setup({
  "isaac10Instance": isaac10,
  "fetchTemplate": "bootstrap3",
  "locale": "de"
}).render("#isaac10-ui");
```

> Rendering

```html
<div id="isaac10-ui"></div>
```


### Embedding and Initialization

To be able to use the _isaac10 UI_, the JavaScript library of _isaac10_ must be loaded as well.
Embedding in an HTML file: see right side.

Initialization of the _isaac10 UI_ objects and rendering of the website: see JavaScript tab.

### Configuration

Parameter | Description | Possible Values
----------|-------------|----------------
**isaac10Instance** | | An instance of `isaac10`.
**fetchTemplate** | those HTML templates (or handlebar templates) to be rendered | <ul> <li>false (no templates will be loaded)</li> <li>"bootstrap3"</li> </ul>
**overrideTranslations** | [Overwriting and Adding Translations](#overwriting-and-adding-translations) |  A JavaScript object, structured like a translation file.
**locale** | Language, displayed in the _isaac10 UI_ | <ul> <li> "de" (german) </li> <li>"en" (english)</li> </ul> More languages can be added through **overrideTranslations**.


### Display of a Page

The call of `render()` includes the _isaac10 UI_ within the HTML element, referenced through a JQuery selector (as shown in the given example: the element with ID "isaac10-ui"). The element should be a `div()` tag.


### Rendering an isaac10 UI page

Which page to be rendered is controlled through an URL anchor. If the _isaac10 UI_ is rendered in the URL without an anchor, only a test page will be created, displaying "_isaac10-UI_ works!"  

The following pages are displayable through _isaac10 UI_:    
<ul>
<li> the [Registration Page for new Customers](#registration-page-for-new-customers)</li>
<li> Overview and forms for account data  </li>
<li>  bills overview  </li>
<li>  subscriptions overview and forms to have the subscriptions managed  </li>
</ul>
