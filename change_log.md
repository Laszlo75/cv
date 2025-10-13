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

## Update to FontAwesome 0.6.0 (Font Awesome 7)

Updated the template to use FontAwesome 0.6.0, which is based on Font Awesome 7:

1. Changed import to `@preview/fontawesome:0.6.0` in `typst-template.typ`
2. Updated font reference from "Font Awesome 6 Brands" to "Font Awesome 7 Brands" in the `parse_icon_string` function

**Important**: FontAwesome 0.6.0 requires Font Awesome 7 fonts to be installed on your system:
- Download from https://fontawesome.com/download
- Install the OTF files for "Font Awesome 7 Free" and "Font Awesome 7 Brands"

If you see warnings like "unknown font family: font awesome 7 free" or "unknown font family: font awesome 7 brands", it means these fonts are not installed on your system. The CV will still compile using fallback rendering, but for proper icon display, you should install the Font Awesome 7 fonts.
