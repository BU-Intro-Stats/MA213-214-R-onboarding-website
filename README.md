# R Onboarding Guide

An introductory R and RStudio website for Boston University introductory statistics courses.

The guide assumes no previous programming experience and introduces students to RStudio, scripts, Quarto, files and folders, CSV data, basic results, troubleshooting, and optional Docker-based workflows.

## Website

[Open the published R Onboarding Guide](https://bu-intro-stats.github.io/R_Onboarding/)

## Lessons

| Lesson | Topic |
|---|---|
| 0 | Installing R and RStudio |
| 1 | Getting familiar with RStudio |
| 2 | Creating your first R script |
| 3 | R Markdown and Quarto |
| 4 | Running code in RStudio |
| 5 | Working with files and folders |
| 6 | Downloading a CSV dataset |
| 7 | Importing data into R |
| 8 | Getting results |
| 9 | Common problems and solutions |
| 10 | Quick reference cheat sheet |
| 11 | Installing and setting up Docker *(optional)* |

## Prerequisites

To work through the core lessons, install:

1. [R](https://cran.r-project.org/)
2. [RStudio Desktop](https://posit.co/download/rstudio-desktop)

Install R before RStudio. Docker is not required for the core R lessons; install [Docker Desktop](https://docs.docker.com/get-started/introduction/get-docker-desktop/) only when a course or project asks you to use containers.

## Project Layout

```text
R_Onboarding/
├── index.qmd                 # Website home page
├── 00-*.qmd ... 11-*.qmd     # Lesson pages
├── full-guide.qmd            # Combined PDF guide source
├── _quarto.yml               # Website and render configuration
├── styles.css                # Website styling
├── img/                      # Images used by the lessons
└── _site/                    # Rendered website output
```

The lesson order, page titles, and sidebar navigation are controlled in `_quarto.yml`. When adding a lesson, add its `.qmd` file to both the `project.render` list and the sidebar `contents` list.

## Render the Website Locally

From the project folder, run:

```sh
quarto render
```

The generated website is written to `_site/`. To preview the site while editing and automatically reload changes:

```sh
quarto preview
```

To render one lesson:

```sh
quarto render 11-docker.qmd
```

## Create the PDF Guide

To render the complete guide as a single PDF:

```sh
quarto render full-guide.qmd --to pdf
```

This creates `R-Onboarding-Guide.pdf`. PDF rendering may require a LaTeX installation, such as TinyTeX. Individual lessons can also be rendered as PDFs:

```sh
quarto render 00-Install-rstudio.qmd --to pdf
quarto render 01-rstudio.qmd --to pdf
quarto render 02-first-script.qmd --to pdf
quarto render 03-quarto-rmarkdown.qmd --to pdf
quarto render 04-running-code.qmd --to pdf
quarto render 05-files-folders.qmd --to pdf
quarto render 06-download-csv.qmd --to pdf
quarto render 07-importing-data.qmd --to pdf
quarto render 08-getting-results.qmd --to pdf
quarto render 09-common-problems.qmd --to pdf
quarto render 10-cheatsheet.qmd --to pdf
quarto render 11-docker.qmd --to pdf
```

## Publishing

The GitHub Actions workflow in `.github/workflows/publish.yml` renders the Quarto site and publishes `_site/` to GitHub Pages whenever changes are pushed to `main`. It can also be started manually from the repository's **Actions** tab.

## Contributing

When editing a lesson:

- Keep examples beginner-friendly and runnable from a clean R session.
- Use relative paths for images and data files.
- Update `_quarto.yml` when adding or renaming pages.
- Run `quarto render` before committing.
- Check the rendered page for broken links, code formatting, and image layout.
- Do not commit personal files such as `.DS_Store`, `.Rhistory`, or local credentials.

## License

See [LICENSE](LICENSE) for licensing information.
