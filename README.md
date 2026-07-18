# Henry's ABC Music Collection

[![ABC Notation](https://img.shields.io/badge/Format-ABC%20Notation-ff69b4.svg?style=flat-square)](https://abcnotation.org/)

This repository serves as a personal archive for my collection of music written in ABC notation.

This collection is a personal project, documenting various musical pieces I have collected or composed. The files within this repository are in ABC format, a simple text-based notation system for representing music.

## Getting Started

If you are new to ABC notation, you can find a basic guide here: [ABC Notation Guide](https://abcnotation.org/).

To view or play the music, you will need an ABC notation reader or software. Many online tools and dedicated programs can interpret these files.

## CI Pipeline

This repository includes a GitHub Actions workflow that automatically builds ABC files into PDFs. The PDFs are stored in the `assets/pdf/` directory and are updated on every push to the main branch.

For more information about the workflow, see [docs/abc-to-pdf-workflow.md](docs/abc-to-pdf-workflow.md).

## Manual Conversion

If you need to manually convert ABC files:

```bash
# Install required tools
sudo apt-get install lilypond

# Convert a single file
abc2ly input_file.abc > output_file.ly
lilypond output_file.ly
```

## Contents

The repository contains various ABC files. I'll figure out how to structure them at some point

## Contributing

This is a personal collection, but if you find a piece you'd like to share, put in a pull request and I'll review it. Please ensure that any contributions adhere to the ABC notation standards.

## About Me

I'm Henry, and this collection is a personal project which seeks to share and archive the very culturally diverse world of music I've come across personally. The starting point however, was the University of Warwick Folk group's band folder.