# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a CV project built with Quarto and R, using the `kazuyanagimoto/awesomecv` Typst extension to generate a professional CV in PDF format. The project leverages the `typstcv` R package for structured CV data handling and formatting.

## Architecture

- **Main CV document**: `cv.qmd` - Quarto document with R code chunks that dynamically generate CV sections
- **Configuration**: `_quarto.yml` - Quarto project configuration
- **Extension**: `_extensions/kazuyanagimoto/awesomecv/` - Custom Typst extension for CV styling
- **Data**: `assets/data/` - Contains CV data files and bibliography
- **Output**: `cv.pdf` - Generated PDF output

The project follows a data-driven approach where CV content is defined in R data frames within the Quarto document, then formatted using the `typstcv` package functions like `resume_entry()` and `format_date()`.

## Common Commands

### Building the CV
```bash
quarto render cv.qmd
```

### Preview during development
```bash
quarto preview cv.qmd
```

### Render to specific format (if needed)
```bash
quarto render cv.qmd --to awesomecv-typst
```

## Key Dependencies

- **Quarto**: Requires version >=1.4.0 (project uses 1.8)
- **R packages**: `typstcv` (from kazuyanagimoto.r-universe.dev)
- **Typst extension**: awesomecv-typst format
- **FontAwesome**: Version 0.5.0 (updated from 0.1.1 for Quarto 1.8 compatibility)

## Important Notes

- The project has been updated to work with Quarto 1.8 and FontAwesome 0.5.0
- The extension uses Typst template files with specific formatting for CV sections
- CV data is embedded directly in the main document as R data frames
- Bibliography is handled via Typst with `assets/my-publication-list.bib`
- The project generates a single PDF output optimized for professional CV presentation

## Development Workflow

1. Edit CV content in `cv.qmd` by modifying the data frames in R code chunks
2. Use `quarto render cv.qmd` to generate the updated PDF
3. Review the generated `cv.pdf` for formatting and content accuracy