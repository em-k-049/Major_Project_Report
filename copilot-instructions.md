---
name: BMSIT Thesis Project
description: "LaTeX thesis writing project with guidelines for chapter structure, bibliography management, formatting, and compilation"
---

# BMSIT Thesis Project - Agent Instructions

## Project Overview
This is a BMSIT (Bangalore Institute of Technology) Master's thesis project implemented in LaTeX. The thesis follows institutional formatting standards and best practices for academic report writing.

## Document Structure
- **Thesis.tex**: Main document - entry point for compilation
- **Chapters**: Chapter1-6 contain thesis content
- **Front Matter**: Abstract and Acknowledgement sections
- **Appendices**: Appendix1 and Appendix2 for supplementary material
- **References**: Bibliography and BibTeX files
- **StyleFiles**: Custom LaTeX classes and institutional style files
- **Macros**: Custom commands and formatting macros
- **ThesisFigs**: All figures, images, and graphics

## When Writing Chapters

### File Organization
- Each chapter is in its own folder with .tex files
- Follow `\chapter{Title}` → `\section{}` → `\subsection{}` hierarchy
- Use `\label{}` consistently for all headings and figures
- Reference labels with `\ref{}` or `\nameref{}`

### Content Guidelines
- Formal academic tone
- Active voice where appropriate
- Define all acronyms on first use: "Machine Learning (ML)"
- Keep paragraphs to 4-5 sentences
- Start each chapter with introduction, end with conclusion/transition

### Citations & References
- Use consistent citation style throughout
- All citations must reference entries in References/*.bib
- Run full bibliography cycle after adding new citations
- Check Thesis.blg for bibliography compilation errors

## When Managing Bibliography

### Citation Keys
Format: `LastnameYear` (e.g., `Smith2020`, `Johnson2019ML`)
- No spaces or special characters
- Consistent capitalization
- Descriptive when multiple papers by same author same year

### Required Fields per Entry Type
- **Articles**: author, title, journal, year, volume, pages, doi
- **Books**: author, title, publisher, year
- **Conference**: author, title, booktitle, year, pages
- **Online**: author/organization, title, url, year, urldate

### Adding New References
1. Create BibTeX entry in References/ with proper formatting
2. Use entry in document with `\cite{key}`
3. Recompile: pdflatex → bibtex → pdflatex (2x)
4. Verify citation appears in bibliography

## When Building/Compiling

### Standard Build
```bash
pdflatex Thesis.tex
```

### Full Build (with bibliography)
```bash
pdflatex Thesis.tex && bibtex Thesis && pdflatex Thesis.tex && pdflatex Thesis.tex
```

### Recommended: latexmk
```bash
latexmk -pdf Thesis.tex        # Single pass
latexmk -pdf -pvc Thesis.tex   # Watch mode (auto-recompile)
```

### Clean & Rebuild
```bash
latexmk -C Thesis.tex && latexmk -pdf Thesis.tex
```

## Formatting & Style Standards

### Text Formatting
- **Emphasis**: `\emph{text}` (italics)
- **Strong**: `\textbf{text}` (bold)
- **Code/Tech terms**: `\texttt{code}`
- **Acronyms**: Define on first use, use acronym package if available

### Figures
- Always include captions: `\caption{Descriptive caption}`
- Include label: `\label{fig:descriptive_name}`
- Reference in text: `As shown in Figure~\ref{fig:name}...`
- Size appropriately: `\includegraphics[width=0.8\textwidth]{path}`

### Tables
- Include descriptive captions
- Label: `\label{tab:name}`
- Reference: `Table~\ref{tab:name} shows...`
- Use consistent formatting for all table content

### Equations
- Inline: `$E = mc^2$`
- Display (numbered): `\begin{equation} ... \end{equation}` with `\label{eq:name}`
- Display (unnumbered): `\[ ... \]`

### Lists
- **Bulleted**: `\begin{itemize} \item ... \end{itemize}`
- **Numbered**: `\begin{enumerate} \item ... \end{enumerate}`
- **Description**: `\begin{description} \item[term] ... \end{description}`

## BMSIT-Specific Requirements

### Style Compliance
- Follow institutional style file in StyleFiles/ folder
- Use required title page format from CertificateGuide/
- Include all required sections: Abstract, Acknowledgement, Chapters, Appendices, References
- Verify with advisor/department guidelines before final submission

### Thesis Structure
1. Title Page (from CertificateGuide/)
2. Abstract
3. Acknowledgement
4. Table of Contents (auto-generated)
5. List of Figures (auto-generated)
6. List of Tables (auto-generated)
7. Chapters 1-6
8. Appendices (as needed)
9. References/Bibliography

### Spacing & Layout
- Default: 1.5 line spacing or as per guidelines
- Margins: Follow institution requirements in style file
- Page numbering: Roman (i, ii, iii) for front matter, Arabic (1, 2, 3) for chapters
- Headers/Footers: Consistent throughout document

## Troubleshooting

### Compilation Issues
| Issue | Solution |
|-------|----------|
| Undefined references | Recompile 2-3 times or use latexmk |
| Missing citations | Run bibtex and recompile 3 passes |
| Figure not found | Check path is relative to Thesis.tex |
| Bibliography errors | Check Thesis.blg for format issues |
| Package conflicts | Review StyleFiles/ for custom packages |

### Log Files
- **Thesis.log**: Main compilation log - check for Error or Warning
- **Thesis.blg**: Bibliography compilation log - check citation format
- Check Thesis.out for cross-reference issues

## Maintenance

### Before Submission
- [ ] Recompile with clean build: `latexmk -C && latexmk -pdf Thesis.tex`
- [ ] Verify all figures and tables are referenced
- [ ] Check all citations appear in bibliography
- [ ] Review Thesis.log for any warnings
- [ ] Ensure formatting matches institutional style
- [ ] Proofread for typos and consistency
- [ ] Verify acronyms defined on first use
- [ ] Check page numbering is correct

### During Development
- Compile frequently to catch errors early
- Keep chapter files organized and well-structured
- Add labels to all headings and figures
- Maintain consistent terminology throughout
- Use consistent citation style from start

## Tips for Large Documents
- Use `\input{file}` for modular content without page breaks
- Use `\include{file}` when page breaks between sections desired
- Disable unused packages during development for faster compilation
- Consider using separate .tex files per chapter for organization
- Test bibliography early and often to catch format issues

## Helpful Commands

### Word Count
```bash
texcount -total Thesis.tex
```

### Find Undefined References
```bash
grep -i "undefined" Thesis.log
```

### View Compilation Warnings
```bash
grep -i "warning" Thesis.log | head -20
```
