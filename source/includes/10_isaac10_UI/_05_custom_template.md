## Apply custom Templates

```html
<script type="text/x-handlebars"
        data-template-name="isaac10-ui/components/div-accountDataFields">
  // Embed the handlebars template for the account data fields component here.
  //
  // The component used when fetching the Bootstrap 3 templates is shown below
  // as an example.
</script>
```

```handlebars
{{! isaac10-ui/components/div-accountDataFields}}

<div class="{{if errors.email 'has-error'}}">
  <label for="emailField">
    {{t 'components.divAccountDataFields.emailLabel'}}
  </label>
  {{input type="text" value=email id="emailField"}}
  {{#if errors.email}}
    <div class="error">{{errors.email}}</div>
  {{/if}}
</div>
```

You also can integrate the _isaac10 UI_ forms as blank pages in case you prefer to use your own templates. Therefore you must initiate the _isaac10 UI_ with `fetchTemplate: false`. As a result none of the templates will be reloaded and forms will be rendered to the given HTML element which has to contain the handlebars elements. These elements need to have the format to be seen on the right side.

Some CSS classes are already implicated (like `'has-error‘`). All elements can easily be modified with own CSS classes e.g. for validation failure for the foundation CSS framework (see right side).
