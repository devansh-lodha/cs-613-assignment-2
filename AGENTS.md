# Communication and Style

- Write in a direct, concise, information-dense, and technical manner.
- Keep language simple, clear, minimal, and easy to understand with logical progression and zero redundancy.
- Do not use emojis, em-dashes, fluff, filler, or marketing language.
- Avoid fancy bullet formatting, especially bold prefixes or titles at the beginning of bullet points. Use plain, simple bullets.
- Use inclusive, modern terminology at all times.
- Focus on understanding and applying underlying core concepts rather than surface jargon.
- Aim for the shortest possible output that completely satisfies all requirements.

# Repository and Environment Management

- Keep this file lean. Only add new guidelines or project instructions with explicit user permission.
- Keep .gitignore minimal. Only add entries when required and do not bloat it.
- Use conventional commits for all git commit messages.
- Do not commit compiler output or temporary LaTeX files (.aux, .bbl, .blg, .log, .out, .fls, .fdb_latexmk, .synctex.gz, .pdf).
- Use a project-local temp/ directory as an ephemeral scratchpad and delete it after task completion. Never use system /tmp/.
- This repository synchronizes directly with an Overleaf project via GitHub. Every change must remain strictly compatible with Overleaf.
- Overleaf projects use LuaLaTeX as the selected compiler engine with main.tex as the main document.
- File system paths and asset file names are case-sensitive on Overleaf Linux containers. Match exact case when referencing images, bib files, and tex source files.
- Verify every document change compiles cleanly with latexmk -lualatex -interaction=nonstopmode main.tex before completing a task.

# Document Architecture and Style Files

- Never modify acl.sty or acl_natbib.bst under any circumstance.
- Submissions must use the official ACL style files and may not use templates designed for other venues.
- The document class must be \documentclass[11pt]{article}.
- Use main.tex as the primary main document compiled with LuaLaTeX.
- Structure document content modularly inside sections/ using separate section files included into main.tex using \input{sections/...}.
- Store all plots, diagrams, and image assets in figures/, loaded via \graphicspath{{figures/}} declared in main.tex.
- Set document layout strictly on A4 paper format (21 cm by 29.7 cm). Never use any other paper size.
- Maintain standard page margins of exactly 2.5 cm on all four sides (top, bottom, left, right).
- Set text in two columns with column width 7.7 cm, column height 24.7 cm, and inter-column separation 0.6 cm.
- Center the paper title, author block, and full-width figures or tables across both columns.
- Ensure all text, tables, and figures fit completely within margins without overflowing.
- Ensure all necessary fonts are embedded directly within the generated PDF.
- Use package microtype to improve text layout and save space.
- Use package inconsolata for typewriter font styling.
- Use package graphicx for image inclusion.
- If compiling under pdfLaTeX instead of LuaLaTeX, load times, latexsym, [T1]{fontenc}, and [utf8]{inputenc}.

# Multilingual and Indic Setup in LuaLaTeX

- For multilingual and non-Latin script processing in LuaLaTeX, use package babel with \usepackage[english,bidi=default]{babel}.
- Set main Roman body font via \babelfont{rm}{TeXGyreTermesX} which provides Times Roman glyphs under LuaLaTeX.
- Never rely on host OS system fonts. macOS ships Apple-specific fonts (such as Kohinoor Devanagari) while Overleaf Linux ships Debian-specific fonts (such as Lohit Devanagari), causing missing-font compilation failures across platforms.
- When Indic or non-Latin scripts are required, place open-source font files (such as Google Noto fonts in TTF or OTF format) directly inside a project-local fonts/ directory tracked in git.
- Load local script fonts in babel using the Path option: \babelfont[*<script>]{rm}[Path=fonts/, BoldFont=<BoldFont>.ttf]{<RegularFont>.ttf}.
- Declare the language locale using \babelprovide[import]{<language>}.
- Wrap non-English text fragments in \foreignlanguage{<language>}{<text>}.
- Alternative multilingual setup can use package polyglossia with \setdefaultlanguage{english} and \setotherlanguages{...}.
- Accompany any text in languages other than English with English translations. Accompany non-Latin scripts with Latin transliterations.

# Submission Modes and Anonymity

- Set submission mode through package options in acl.sty: review, final (no option), or preprint.
- Load review mode via \usepackage[review]{acl}. This enables double-blind reviewing, adds margin line number rulers, centers page numbers in the bottom margin, and masks author details with Anonymous ACL submission.
- Load final mode via \usepackage{acl}. This removes line number rulers, removes page numbers, and displays author names and affiliations.
- Load preprint mode via \usepackage[preprint]{acl}. This displays author names, affiliations, and page numbers.
- For review versions, strictly exclude all identifying information, author names, affiliations, email addresses, project URLs, and acknowledgments.
- For review versions, avoid self-identifying citations such as "we previously showed (Author, 1997)" or anonymous citations like "(Anonymous, 1997)". Use third-person phrasing such as "Author (1997) previously showed".
- Reserve space of 7.5 cm from the top of the first page to the start of the body text in review versions so that author blocks fit seamlessly in final versions.
- If title and author information requires more vertical space, adjust length titlebox using \setlength\titlebox{<dim>} with a dimension of 5 cm or larger.

# Title and Author Formatting

- Typeset document title in title case using APA style capitalization, centered across both columns at 15 pt bold. Do not use all-capital letters except for acronyms (such as BLEU) or proper nouns (such as English).
- Type long titles across two lines without intervening blank lines. Place title 2.5 cm from the top of the page.
- Typeset author names in 12 pt bold. Write full names without abbreviating given names to initials unless customary. Do not capitalize surnames in all caps.
- Typeset author affiliations in 12 pt regular. Include complete address and email address. Never use footnotes for affiliations.
- Separate authors from the same institution using \and.
- Separate authors from different institutions into columns using \And.
- Begin a new row of author columns using \AND.
- Format large multi-author teams using \textsuperscript indicators matching corresponding affiliation lines below.

# Typography and Hierarchy

- Typeset section titles in 12 pt bold with Arabic numerals (e.g., 1 Introduction).
- Typeset subsection titles in 11 pt bold with dot notation (e.g., 2.1 Model Architecture).
- Typeset body paragraphs in 11 pt regular single-spaced. Indent new paragraphs by 0.4 cm, except for the first paragraph directly following a section heading.
- Typeset abstract title centered in 12 pt bold above the abstract body. Typeset abstract text in 10 pt regular single-spaced with margins indented 0.6 cm on both left and right sides.
- Keep the abstract as a concise summary of the thesis and conclusions under 200 words.
- Typeset footnotes in 9 pt regular at the bottom of the page, separated from body text by a horizontal rule.
- Format within-document and external hyperlinks in dark blue (hex #000099) without boxes or underlines.
- If a citation splits across a page boundary, older compilers may raise the error: pdfendlink ended up in different nesting level than pdfstartlink. Fix this by rephrasing nearby text so the citation does not straddle the page break.
- Number displayed equations with equation environments (\begin{equation} ... \end{equation}) and cross-reference them using \ref or \eqref.
- Define labels on sections, subsections, figures, tables, and equations with \label{<key>} and cross-reference with \ref{<key>}.

# Page Limits and Sections

- Review versions of long papers allow up to 8 pages of content, plus unlimited pages for references.
- Final versions of long papers allow up to 9 pages of content, plus unlimited pages for acknowledgments and references.
- Review versions of short papers allow up to 4 pages of content, plus unlimited pages for references.
- Final versions of short papers allow up to 5 pages of content, plus unlimited pages for acknowledgments and references.
- All figures and tables belonging to the main body text must fit within these specified page limits.
- Limitations section is mandatory for ACL submissions, placed unnumbered using \section*{Limitations} after the conclusions, and does not count against page limits.
- Acknowledgments section is unnumbered, placed using \section*{Acknowledgments} immediately before references, and must be omitted from review versions.
- References section is unnumbered, generated using \bibliography{...}, and placed immediately before any appendices.
- Appendices follow the references section, initiated by the \appendix command which converts section numbering into sequential capital letters (e.g., Appendix A).
- Appendices contain non-critical proofs, derivations, lemmas, and extended data tables. Review versions of appendices must remain strictly anonymous.
- Supplementary material such as standalone code and datasets must be uploaded separately, documented with licenses and replication instructions, and remain self-contained without making the main paper dependent on unreviewed details.

# Tables, Figures, and Accessibility

- Position tables and figures close to their first point of mention in the body text.
- Center tables and figures with \centering.
- Use single-column floats (figure, table) by default. Use starred two-column environments (figure star, table star) for wide elements spanning both columns.
- For side-by-side subfigures within a two-column float, use \includegraphics[width=0.48\linewidth]{...} \hfill \includegraphics[width=0.48\linewidth]{...} inside \begin{figure*}.
- Scale image widths explicitly with graphicx options such as [width=\columnwidth] or [width=\linewidth].
- Provide a numbered caption below every figure and table (e.g., Figure 1: Caption, Table 1: Caption).
- Center single-line captions. Left-align captions spanning more than one line.
- Never override or customize default caption font sizes, dimensions, or spacing.
- Ensure all figures and tables maintain complete readability in grayscale. Do not use color as the sole means of conveying essential distinctions.
- Conform fonts within figures to document fonts as closely as possible.

# Citations and ACL Bibliography

- Maintain custom bibliography entries in references.bib following APA format.
- Format in-text narrative citations with \citet{<key>} to produce Author (Year).
- Format parenthetical citations with \citep{<key>} to produce (Author, Year).
- Format citations inside existing parentheses with \citealp{<key>} to produce Author, Year without outer parentheses.
- Format possessive citations with \citeposs{<key>} to produce Author's (Year).
- Format year-only parenthetical citations with \citeyearpar{<key>} to produce (Year).
- Include references in the bibliography without in-text citation using \nocite{<key>}.
- Never use parenthetical citations as syntactic nouns or subjects within a sentence.
- Cite two authors using both names joined by "and" (e.g., Aho and Ullman, 1972). Cite three or more authors using the first author followed by "et al." (e.g., Chandra et al., 1981).
- Append lowercase letters to publication years to disambiguate works by the same authors published in the same year.
- Collapse multiple citations into a single \citep command separated by commas (e.g., \citep{key1,key2}).
- Reference the refereed archival publication version when a paper has appeared in multiple venues.
- Alphabetize references by the surname of the first author. Write full author names rather than initials. Do not rely on automated citation indices.
- Include DOI or URL fields for every reference entry whenever available. Titles link automatically when DOI or URL fields exist.
- Accented characters in BibTeX entries must use standard TeX macros ({\\"a}, {\\^e}, {\\`i}, {\\.I}, {\\o}, {\\'u}, {\\aa}, {\\c c}, {\\u g}, {\\l}, {\\~n}, {\\H o}, {\\v r}, {\\ss}) to maintain proper alphabetical ordering.
- ACL Anthology semantic bibkeys follow the convention {names}-{year}-{words}, where names is concatenated surnames for 1 to 2 authors or lastname-etal for 3 or more authors, year is a four-digit year, and words represents significant title words (e.g., galley-etal-2004-whats).
- To respect Overleaf's 50 MB bib file size limit, use sharded anthology files (anthology-1.bib, anthology-2.bib) downloaded from aclanthology.org via external URL.
- Load sharded anthology files alongside custom entries using \bibliography{references,anthology-1,anthology-2}.
