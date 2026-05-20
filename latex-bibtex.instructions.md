---
name: LaTeX Bibliography & Citation Management
description: "Use when: managing BibTeX references, fixing citation issues, updating bibliography, managing .bib files, or handling citation formats"
applyTo: "References/**/*.bib"
---

# BibTeX & Citation Management Guide

## Bibliography File Structure

Located in: `References/`

### Supported Entry Types
```bibtex
@article{key, author, title, journal, year, volume, pages}
@book{key, author, title, publisher, year}
@inproceedings{key, author, title, booktitle, year}
@thesis{key, author, title, school, year}
@misc{key, author, title, howpublished, year}
@techreport{key, author, title, institution, year}
```

## Citation Best Practices

### Key Naming Convention
Use format: `LastnameYear` or `LastnameYearKeyword`
- Examples: `Smith2020`, `Smith2020ML`, `Johnson2019DeepLearning`
- Avoid spaces, special characters in keys
- Use consistent capitalization across all entries

### Entry Fields
- **author**: Use "FirstName LastName and FirstName LastName" format
- **title**: Sentence case for articles and papers (capitalize only first word, proper nouns)
- **year**: Use 4-digit year (YYYY)
- **journal/booktitle**: Full name or standard abbreviation
- **volume**: Issue number format (e.g., "10(2)" for volume 10, issue 2)
- **pages**: Range format "start--end" (use em-dash, not hyphen)
- **url**: Include with `urldate = {YYYY-MM-DD}` for online sources
- **doi**: Preferred for journal articles over URL

## Citation Styles in Thesis

### Default Style: BMSIT Standard
Check `StyleFiles/` for the active `.bst` (BibTeX Style) file.

### Using Citations in LaTeX
```tex
% Inline citation (author-year)
\cite{Smith2020}

% Narrative citation
\citet{Smith2020} showed that...

% Parenthetical citation
This result is well-known \citep{Smith2020}.

% Multiple citations
\cite{Smith2020,Johnson2019,Brown2021}
```

## Common Bibliography Issues & Solutions

### Citation Not Appearing
1. Verify entry exists in `.bib` file with exact key match
2. Run: `pdflatex Thesis.tex` → `bibtex Thesis` → `pdflatex Thesis.tex` (2x)
3. Check `Thesis.blg` for BibTeX errors
4. Ensure `\bibliography{References/YourBibFile}` in Thesis.tex

### "Unknown entry type" Error
- Verify entry type is supported by current `.bst` file
- Check for typos in `@article`, `@book`, etc.
- Refer to `.bst` documentation for unsupported types

### Malformed Entry
- Missing required fields (author, title, year minimum)
- Unescaped special characters: Use `\'{e}` for accents, `\&` for ampersand
- Mismatched braces: Every `{` must have matching `}`
- Commas: Each field except last must end with comma

### Style Mismatch
- Check active `.bst` file matches thesis requirements
- Verify all entries match expected format for selected style
- Some styles require capitalization in title: Use `{Title Here}` to protect caps

## Workflow: Adding New Reference

1. **Gather Information**
   - Author(s), year, title, publication details
   - DOI or URL if available

2. **Create BibTeX Entry**
   ```bibtex
   @article{NewAuthor2024,
     author = {First Last and Second Author},
     title = {Paper Title in Sentence Case},
     journal = {Journal Name},
     year = {2024},
     volume = {15},
     pages = {123--145},
     doi = {10.xxxx/xxxxx}
   }
   ```

3. **Add to Bibliography**
   - Add entry to appropriate `.bib` file in References/
   - Follow existing formatting conventions
   - Verify entry matches required citation style

4. **Use in Document**
   ```tex
   \cite{NewAuthor2024}
   ```

5. **Recompile**
   ```bash
   pdflatex Thesis.tex
   bibtex Thesis
   pdflatex Thesis.tex
   pdflatex Thesis.tex
   ```

## Citation Format Requirements by Type

### Journal Articles
```bibtex
@article{Sample2020,
  author = {John Smith and Jane Doe},
  title = {Research finding title},
  journal = {Journal Name},
  year = {2020},
  volume = {10},
  number = {3},
  pages = {100--115},
  doi = {10.xxxx/journal.2020.xxxxx}
}
```

### Conference Papers
```bibtex
@inproceedings{Sample2020,
  author = {John Smith},
  title = {Paper title},
  booktitle = {Proceedings of Conference Name},
  year = {2020},
  pages = {200--210},
  organization = {IEEE}
}
```

### Books
```bibtex
@book{Sample2019,
  author = {John Smith},
  title = {Book Title},
  publisher = {Publisher Name},
  year = {2019},
  edition = {2nd}
}
```

### Thesis/Dissertation
```bibtex
@phdthesis{Sample2018,
  author = {John Smith},
  title = {Thesis Title},
  school = {University Name},
  year = {2018}
}
```

### Online Resources
```bibtex
@misc{Sample2023,
  author = {John Smith},
  title = {Web Page Title},
  howpublished = {\url{https://example.com/page}},
  year = {2023},
  urldate = {2023-12-15}
}
```

## Bibliography Maintenance Checklist
- [ ] All cited references are in `.bib` file
- [ ] All entries in `.bib` are cited in document
- [ ] No duplicate entries with same content
- [ ] Consistent author name formatting
- [ ] Consistent title capitalization
- [ ] DOI included for journal articles (when available)
- [ ] All required fields present for each entry type
- [ ] No special characters without proper escaping
