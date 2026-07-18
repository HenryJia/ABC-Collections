# ABC to PDF Conversion Workflow

This document explains how the GitHub Actions workflow converts ABC notation files into PDFs.

## Overview

The workflow automatically converts ABC files stored in `assets/abc/` directory into PDF format and stores them in `assets/pdf/`. This ensures that musical compositions are available in both text (ABC) and printable (PDF) formats.

## Workflow Steps

1. **Checkout Repository**: Clones the repository to the runner
2. **Install Dependencies**: Installs required tools:
   - `abcm2ps`: ABC to PostScript converter
   - `ghostscript`: PostScript processing tools
3. **Convert ABC to PDF**:
   - For each `.abc` file in `assets/abc/`:
     - Converts the ABC file to PostScript format using `abcm2ps`
     - Converts the PostScript file to PDF format using `ps2pdf`
     - Moves the generated PDF to `assets/pdf/`
4. **Commit and Push**: Commits any new or updated PDF files

## Tools Used

- **abcm2ps**: Converts ABC notation directly to PostScript format
- **Ghostscript**: PostScript processing tools for PDF conversion
- **ps2pdf**: Converts PostScript files to PDF format

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
sudo apt-get install abcm2ps ghostscript

# Test conversion of a single file
abcm2ps assets/abc/WarwickFolk-Treble.abc -O test-output.ps
ps2pdf test-output.ps assets/pdf/test-output.pdf
```

## Troubleshooting

If the workflow fails:
1. Check that ABC files are valid and properly formatted
2. Verify that required tools are available in the environment
3. Ensure sufficient disk space for PDF generation
4. Note: The workflow ignores conversion errors to prevent build failures from malformed ABC files