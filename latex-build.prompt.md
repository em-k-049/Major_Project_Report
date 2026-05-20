---
name: Build LaTeX Thesis
description: "Quick compilation workflow for Thesis.tex with options for clean builds, bibliography updates, and error diagnosis"
---

# Build LaTeX Thesis

## Quick Build
Compile with: `pdflatex Thesis.tex`

## Full Build (with bibliography)
Run in order:
1. `pdflatex Thesis.tex`
2. `bibtex Thesis`
3. `pdflatex Thesis.tex`
4. `pdflatex Thesis.tex`

## Recommended: Using latexmk
Automatically handles all compilation passes:
```bash
latexmk -pdf Thesis.tex
```

## Clean Build
Remove auxiliary files and rebuild:
```bash
latexmk -C Thesis.tex      # Remove all generated files except PDF
latexmk -pdf Thesis.tex    # Rebuild from scratch
```

## Troubleshooting

### Check Compilation Errors
- View `Thesis.log` for pdflatex errors
- View `Thesis.blg` for BibTeX errors
- Search for "Error" or "undefined" in log files

### Common Fixes
- **Undefined references**: Recompile 2-3 times
- **Missing citations**: Run bibtex and recompile
- **Figure not found**: Verify path is relative to Thesis.tex
- **Package errors**: Check StyleFiles/ for custom packages

### Watch Mode (live compilation)
```bash
latexmk -pdf -pvc Thesis.tex
```
Automatically recompiles on file changes.
