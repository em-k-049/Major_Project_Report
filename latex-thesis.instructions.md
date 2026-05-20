---
name: LaTeX Thesis Writing
description: "Use when: editing .tex files, writing chapters, managing citations, formatting thesis content, or building LaTeX documents"
applyTo: "**/*.tex"
---

# LaTeX Thesis Writing Guide

## Project Structure
- **Thesis.tex**: Main document file (entry point)
- **Chapter1-6/**: Individual chapter folders
- **Abstract/, Acknowledgement/**: Front matter
- **Appendix1, Appendix2/**: Appendices
- **References/**: Bibliography and references
- **StyleFiles/**: Custom LaTeX classes and packages
- **Macros/**: Custom command definitions
- **ThesisFigs/**: Figure and image files

## Chapter Guidelines

### File Organization
Each chapter should follow this structure:
```tex
\chapter{Chapter Title}
\label{ch:chapter_name}

\section{First Section}
\label{sec:section_name}
Content here...

\subsection{Subsection}
\label{subsec:subsection_name}
```

### Cross-References
- Use `\label{}` immediately after chapter/section headings
- Reference with `\ref{}` or `\nameref{}` for clarity
- Format: `ch:`, `sec:`, `subsec:`, `fig:`, `tab:`, `eq:` prefixes

### Citations
- Maintain consistency with existing bibliography style
- Use `\cite{}` for inline citations
- Check References/ folder for current citation format
- Reference entries should follow: Author, Year, Title format

## Common Commands & Patterns

### Text Formatting
- Emphasis: `\emph{text}` (preferred over `\textit{}`)
- Strong: `\textbf{text}`
- Code/monospace: `\texttt{text}`
- Small caps: `\textsc{text}`

### Equations
- Inline: `$equation$`
- Display: `\[equation\]` or equation environment
- Numbered: `\begin{equation}...{equation}` with `\label{eq:name}`

### Figures & Tables
- Always include captions
- Use `\includegraphics[width=0.8\textwidth]{path}` for sizing
- Wrap in figure/table environments with labels
- Reference via `\ref{fig:name}` or `\ref{tab:name}`

### Lists
- Itemized: `\begin{itemize}...\end{itemize}`
- Enumerated: `\begin{enumerate}...\end{enumerate}`
- Description: `\begin{description}...\end{description}`

## Best Practices

### Structure
1. Keep chapters under 5,000 words for maintainability
2. Start each chapter with an introduction paragraph
3. Use consistent heading hierarchy (chapter → section → subsection)
4. End chapters with brief conclusion or transition

### Content
- Write in formal academic tone
- Use active voice where possible
- Define acronyms on first use (e.g., "Machine Learning (ML)")
- Keep paragraphs to 4-5 sentences maximum

### References
- Use consistent citation style throughout
- Include all referenced works in bibliography
- Avoid self-plagiarism by paraphrasing appropriately
- Include DOI or URL for online sources when available

### Formatting
- Maintain consistent spacing (single or 1.5 line spacing as required)
- Use consistent indent styles
- Keep line length readable (60-80 characters for source)
- Use proper typography (em-dash `---`, not hyphen)

## Building the Document

### Compilation Commands
```bash
# Single compile
pdflatex Thesis.tex

# With bibliography
pdflatex Thesis.tex
bibtex Thesis
pdflatex Thesis.tex
pdflatex Thesis.tex

# Using latexmk (recommended)
latexmk -pdf Thesis.tex
```

### Clean Build
```bash
# Remove auxiliary files
latexmk -c Thesis.tex

# Remove all generated files except PDF
latexmk -C Thesis.tex
```

## Troubleshooting

### Common Issues
- **Missing chapter file**: Check path in `\input{}` or `\include{}` commands in Thesis.tex
- **Citation not appearing**: Run bibtex and recompile (3 passes minimum)
- **Broken references**: Recompile twice to update all labels
- **Figure not showing**: Verify image path is relative to Thesis.tex location
- **Bibliography style mismatch**: Check `.bst` file in References/ folder

### Log Files to Check
- `Thesis.log`: General compilation errors
- `Thesis.blg`: Bibliography processing errors
- `.synctex.gz`: For forward/inverse search in PDF viewers

## BMSIT Thesis Requirements
- Conform to institutional style guide in StyleFiles/
- Include proper abstract and acknowledgement
- Follow citation format specified by advisor/department
- Ensure all figures and tables are referenced in text
- Maintain consistent terminology throughout

## Tips for Large Documents
- Compile frequently to catch errors early
- Use `\input{file}` for organization without page breaks
- Use `\include{file}` when you want page breaks between sections
- Consider using separate .tex files for each chapter
- Disable unused packages during development for faster compilation
