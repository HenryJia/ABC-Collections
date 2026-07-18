# ABC to PDF Conversion Workflow

This document explains how the GitHub Actions workflow converts ABC notation files into PDFs.

## Overview

The workflow automatically converts ABC files stored in `assets/abc/` directory into PDF format and stores them in `assets/pdf/`. This ensures that musical compositions are available in both text (ABC) and printable (PDF) formats.

## Workflow Steps

1. **Checkout Repository**: Clones the repository to the runner
2. **Install Dependencies**: Installs required tools:
   - `lilypond`: Music engraving software
   - `texlive`: LaTeX packages for document formatting
3. **Convert ABC to PDF**:
   - For each `.abc` file in `assets/abc/`:
     - Converts the ABC file to LilyPond format using `abc2ly`
     - Generates a PDF using `lilypond`
     - Moves the generated PDF to `assets/pdf/`
4. **Commit and Push**: Commits any new or updated PDF files

## Tools Used

- **abc2ly**: Converts ABC notation to LilyPond format
- **LilyPond**: Music engraving software that generates high-quality musical scores
- **TeX Live**: LaTeX packages for document formatting

## Directory Structure

```
assets/
├── abc/           # Source ABC files (input)
└── pdf/           # Generated PDF files (output)
```

## Testing the Workflow

To test locally:

```bash
# Install required tools
sudo apt-get install lilypond texlive-latex-base texlive-latex-recommended texlive-fonts-recommended

# Test conversion of a single file
abc2ly assets/abc/WarwickFolk-Treble.abc > test-output.ly
lilypond test-output.ly
```

## Troubleshooting

If the workflow fails:
1. Check that ABC files are valid and properly formatted
2. Verify that required tools are available in the environment
3. Ensure sufficient disk space for PDF generation