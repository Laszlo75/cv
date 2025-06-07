# Curriculum Vitae

This repository contains the source files for building my CV using the [typstcv](https://github.com/kazuyanagimoto/typstcv) extension for Quarto.  The project relies on Quarto's Typst engine and a custom template to create a nicely formatted PDF.

## Repository layout

```
/README.md           – project overview and build instructions
/_quarto.yml         – Quarto project configuration
/cv.qmd              – main document describing the CV
/change_log.md       – notes about template fixes
/_extensions/        – local copy of the `awesomecv-typst` template
/assets/             – bibliographic data and other assets
/cv.pdf              – generated PDF (example output)
```

`cv.qmd` contains the CV data in R code chunks.  The bibliography used in the publications section is stored in `assets/my-publication-list.bib`.

## Requirements

- [R](https://www.r-project.org/) and the **typstcv** package
- [Quarto](https://quarto.org/) v1.4 or later

Install the **typstcv** package from the author's R-universe repository:

```r
install.packages("typstcv", repos = "https://kazuyanagimoto.r-universe.dev")
```

## Building the CV

Run the following command in the project directory to produce `cv.pdf`:

```bash
quarto render cv.qmd
```

The output PDF will be written to the project root.  You can also render the document from R using `quarto::quarto_render("cv.qmd")`.

If you do not have the fonts referenced in `cv.qmd` (e.g. *SF Pro Text*), adjust the `style` section at the top of `cv.qmd` to use fonts available on your system.

## Acknowledgements

The Typst template is based on the `awesomecv-typst` extension by [Kazuharu Yanagimoto](https://github.com/kazuyanagimoto).  The local copy in `_extensions/` includes updates for newer Quarto versions and FontAwesome 0.5.0 – see `change_log.md` for details.
