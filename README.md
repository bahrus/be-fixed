# be-fixed [TODO]

Define local HTML "constants."

## Example 1

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

What this does:

1.  Adds [be-value-added](https://github.com/bahrus/be-value-added) enhancement onto the meta element.
2.  Sets the value to globalThis['apiBase'].

## Example 2.  With free-form JavaScript evaluation, compact notation

The example above allowed us to access a very limited amount of "Javascript" -- limited to field/accessors.

For anything beyond that, we need to explicitly announce that our retrieving of our constant carries a certain amount of risk:


```html
<meta slot=config itemprop=myCustomElementApiBase be-fixed='on load. on load start.' 
    onload="top.querySelector('my-iframe').contentWindow">
```

Supported "events":

onload (after document has loaded)
onloadstart (right away)

## Example 3.  Build constant object;

```html
<meta slot=config itemprop=myCustomElementApiBase be-fixed='on load. on load start.' 
    onload="export const key1 = top.querySelector('my-iframe').contentWindow; export const key2 = ...">
```
