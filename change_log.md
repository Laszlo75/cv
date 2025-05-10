I've successfully fixed the rendering issue in Quarto v1.8. The problem was related to how Typst handles page counters in the newer version of Quarto.

The solution involved two key changes:

1. Added a context wrapper around the page counter in the footer section of the template file:

```typst
footer: context [
  ...
  #counter(page).display()
  ...
]
```

2. Updated the FontAwesome import in the template file to use a newer version:

```typst
#import "@preview/fontawesome:0.5.0": *
```


The problem was that FontAwesome 0.5.0 changed its API compared to version 0.1.1.

The change I made:

1. Updated the `parse_icon_string` function in `_extensions/kazuyanagimoto/awesomecv/typst-template.typ`
2. Changed `fa-set: "Brands"` to `font: "Font Awesome 6 Brands"`

In FontAwesome 0.5.0:

- The parameter name changed from `fa-set` to `font`
- The value needs to be the full font name "Font Awesome 6 Brands" instead of just "Brands"

This change should resolve the error message you were seeing. You can now compile your CV with FontAwesome 0.5.0 without encountering the "unexpected argument: fa-set" error.
