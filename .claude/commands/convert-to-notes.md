---
description: Convert PowerPoint slides to markdown and print-ready PDF with proper formatting
model: haiku
---

# PowerPoint to Markdown/PDF Converter

Convert PowerPoint (.pptx) files into clean markdown notes and print-ready PDFs with proper page breaks.

## Arguments

`$ARGUMENTS` - Path to the PowerPoint file

**Flags:**
- `--output` or `-o`: Output directory (default: same directory as input, in a `notes/` subfolder)
- `--pdf`: Generate PDF in addition to markdown (default: true)
- `--no-pdf`: Skip PDF generation, markdown only
- `--toc`: Include table of contents (default: true for PDF)

**Examples:**
- `/convert-to-notes /path/to/slides.pptx`
- `/convert-to-notes ~/Documents/lecture.pptx --no-pdf`
- `/convert-to-notes ./presentation.pptx -o ~/notes/`

## Process

### Step 1: Extract PowerPoint Content

PowerPoint files are ZIP archives containing XML. Extract and parse:

```bash
# Create temp directory and extract
unzip -o "/path/to/file.pptx" -d /tmp/pptx_extract
```

### Step 2: Parse Slide Content

For each slide XML file in `ppt/slides/`:
- Extract text content by stripping XML tags
- Identify slides with images (check `_rels/slideX.xml.rels` for image references)
- Note slide order from filenames

### Step 3: Create Markdown

Organize content into logical sections:
- Group related slides under headers
- Convert bullet points to markdown lists
- **Create tables where slides contain:**
  - Comparison/contrast content
  - Lists of items with descriptions
  - Stage/phase information
  - Any content that was likely presented as an image/diagram
- Preserve hierarchy (h1, h2, h3 based on content structure)

**Table conversion guidelines:**
- Defense mechanisms, stages of development, personality components → tables
- Lists with descriptions → tables with Name | Description columns
- Processes with steps → tables with Step | Description columns
- Comparisons → tables with appropriate column headers

### Step 4: Generate PDF (if requested)

Use pandoc with LaTeX for print-quality output:

```bash
pandoc "input.md" \
  -o "output.pdf" \
  --pdf-engine=pdflatex \
  -V geometry:margin=1in \
  -V fontsize=11pt \
  -V documentclass=article \
  -V colorlinks=true \
  -V linkcolor=blue \
  --toc \
  --toc-depth=2 \
  -H <(cat <<'EOF'
\usepackage{longtable}
\usepackage{booktabs}
\usepackage{array}
\usepackage{float}
\usepackage{etoolbox}
\renewcommand{\arraystretch}{1.3}
\let\oldlongtable\longtable
\let\endoldlongtable\endlongtable
\renewenvironment{longtable}{\begin{table}[H]\begin{oldlongtable}}{\end{oldlongtable}\end{table}}
\makeatletter
\patchcmd{\@afterheading}{\clubpenalty\@M}{\clubpenalty\@M\@nobreaktrue}{}{}
\makeatother
\widowpenalties 3 10000 10000 150
\clubpenalties 3 10000 10000 150
EOF
)
```

**LaTeX settings explained:**
- `\begin{table}[H]` - Keep tables together, don't float
- `\patchcmd{\@afterheading}` - Prevent page breaks immediately after section titles
- `\widowpenalties/clubpenalties` - Prevent orphan/widow lines, keep titles with content
- `\arraystretch{1.3}` - Better table row spacing

### Step 5: Verify Output

Check the PDF:
```bash
pdfinfo output.pdf | grep -E "Pages|Page size"
```

Report file locations and page count to user.

## Output Format

### Markdown Structure

```markdown
# [Presentation Title]

## [Major Section]

### [Subsection]

Content as paragraphs or lists.

| Column 1 | Column 2 |
|----------|----------|
| Item | Description |

---

## [Next Section]
...
```

### File Naming

- Input: `Lecture Name.pptx`
- Markdown: `lecture-name.md` (lowercase, hyphens)
- PDF: `lecture-name.pdf`

## Requirements

- `pandoc` - for markdown to PDF conversion
- `pdflatex` - LaTeX engine for PDF rendering
- `unzip` - for extracting PPTX contents

Check with:
```bash
which pandoc pdflatex unzip
```

## What This Bot Does

- Extracts all text content from PowerPoint slides
- Identifies image-heavy slides and creates descriptive tables
- Organizes content into clean, hierarchical markdown
- Generates print-ready PDFs with proper page breaks
- Keeps tables together (no mid-table page breaks)
- Prevents sections from starting at bottom of pages
- Includes table of contents for navigation

## What This Bot Does NOT Do

- Extract or embed images from the PowerPoint
- Preserve animations or transitions
- Convert speaker notes (though this could be added)
- Handle password-protected files
