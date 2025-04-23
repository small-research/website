# SMALL Website

This repository contains the source files and code for editing and maintaining the **SMALL** website. Follow the instructions below to update content or publish the site.

## Instructions

- Download the `.bib` file from the [SMALL Google Scholar page](https://scholar.google.com).
- Convert the `.bib` file to `.csv` using [this online BibTeX to CSV converter](https://www.bibtex.com/c/bibtex-to-csv-converter/).
- To publish the website on GitHub Pages:
  1. Navigate to the directory containing the `.qmd` files.
  2. Run the following command in your terminal:
     ```bash
     quarto publish
     ```

## Dependencies

Before publishing, ensure all required Python packages are installed. These are specified in the `pyproject.toml` file. Both `research.qmd` and `people.qmd` include embedded Python scripts that read data from external sources.

You can install the dependencies using one of the following methods:
- **Using `pip`**:
  ```bash
  pip install -r requirements.txt
  ```
- **Using `poetry`**:
  ```bash
  poetry install
  ```
- **Using `conda`**:
  Create the environment:
  ```bash
  conda env create -f small_website.yml
  ```
  Then activate it:
  ```bash
  conda activate <env_name>
  ```
