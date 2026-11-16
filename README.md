# SMALL Website

This repository contains the source files and code for editing and maintaining the **SMALL** website, built with [Quarto](https://quarto.org/). Python dependencies are managed with [uv](https://docs.astral.sh/uv/).

## Requirements

- [Quarto](https://quarto.org/docs/get-started/) (CLI)
- [uv](https://docs.astral.sh/uv/getting-started/installation/):
  ```bash
  curl -LsSf https://astral.sh/uv/install.sh | sh
  ```

`research.qmd` and `people.qmd` run embedded Python at render time, so Quarto needs the project's Python environment (declared in `pyproject.toml` and pinned in `uv.lock`).

## Running locally with uv

1. Create the virtual environment and install the locked dependencies (uv also downloads Python 3.12 if needed):
   ```bash
   uv sync
   ```
2. Start a live preview (opens the site in the browser and reloads on every save):
   ```bash
   uv run quarto preview
   ```
3. Or just build the static site into `_site/`:
   ```bash
   uv run quarto render
   ```

Running Quarto through `uv run` puts `.venv/bin` first on the `PATH`, so Quarto uses the project's Python and Jupyter kernel instead of the system one. Alternatively, activate the environment once (`source .venv/bin/activate`) and call `quarto` directly.

### Managing dependencies

- Add a package: `uv add <package>`
- Remove a package: `uv remove <package>`
- Upgrade the lock file: `uv lock --upgrade`

Commit both `pyproject.toml` and `uv.lock` after changing dependencies — the publish workflow installs with `uv sync --locked` and fails if they are out of sync.

## Updating publications

- Download the `.bib` file from the [SMALL Google Scholar page](https://scholar.google.com/citations?user=MGrbI2UAAAAJ&hl=pt-BR) and save it as `references.bib`.
- Convert it to `references.csv` using [this online BibTeX to CSV converter](https://www.bibtex.com/c/bibtex-to-csv-converter/).

## Publishing

Every push to `main` triggers the GitHub Action in `.github/workflows/publish.yml`, which runs `uv sync --locked`, renders the site and publishes it to the `gh-pages` branch. It can also be started manually from the *Actions* tab (`workflow_dispatch`).

To publish manually from your machine instead:

```bash
uv sync
uv run quarto publish gh-pages
```

## Other environments

`uv` is the recommended setup, but the older alternatives still work:

- **pip**: `pip install -r requirements.txt`
- **conda**: `conda env create -f small_website.yml && conda activate small_website`
