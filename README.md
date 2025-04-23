# SMALL Website

This repository contains the source files and code for editing and maintaining the **SMALL** website. Follow the instructions below to update content or publish the site.

## Instructions

- Download the `.bib` file from the [SMALL Google Scholar page](https://scholar.google.com/citations?user=MGrbI2UAAAAJ&hl=pt-BR).
- Convert the `.bib` file to `.csv` using [this online BibTeX to CSV converter](https://www.bibtex.com/c/bibtex-to-csv-converter/).
- To publish the website on GitHub Pages:
  1. Navigate to the directory containing the `.qmd` files.
  2. Run the following command in your terminal:
     ```bash
     quarto publish
     ```

## Dependencies

- Before publishing, ensure all required Python packages are installed. These are specified in the `pyproject.toml` file.
- Both `research.qmd` and `people.qmd` include embedded Python scripts that read data from external files.
- You can also use the `requirements.txt` file to set up a Conda environment. Convert it using the [`pip2yml`](https://pypi.org/project/pip2yml/) package:
  ```bash
  pip2yml -s --no-pin requirements.txt > environment.yml
  ```

