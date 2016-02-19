## Overwriting and Adding Translations


```javascript
// your translations
var customTranslations = {
  "de": {
    "defaults": {
      "save": "Absenden"
    }
  }
};

// Initializing the JavaScript API
var isaac10 = new Isaac10("ihre-subdomain");

// Initializing the isaac10UI
Isaac10UI.setup({
  "isaac10Instance": isaac10,
  "fetchTemplate": "bootstrap3",
  "locale": "de",
  "overrideTranslations": customTranslations   // <--------------------
}).render("#isaac10-ui");
```


By initializing the _isaac10 UI_ you can overwrite or add translations employing the parameter `overrideTranslations`.
Therefore you need to generate a JavaScript object which has the same structure as the translation file (see JavaScript tab).

You can use the currently used translation file in not minified form (as coffee script) as template to be downloaded here:
[https://app.isaac10.com/ui/translations.coffee](https://app.isaac10.com/ui/translations.coffee)
