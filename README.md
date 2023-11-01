# be-fixed

Define local HTML "constants."

```html
<html>
    <head>
        ...
        <link id=apiBase rel=preconnect href=https://example.com/api>
        ...
    </head>
    <body>
        ...
        <my-custom-element>
            #shadow
                <slot name=config be-prop-slotting></slot>
            <meta slot=config itemprop=myCustomElementApiBase be-fixed='from apiBase:href.'>

    </body>
</html>
```

Note that HTML5 already makes "apiBase" a global constant in JavaScript.