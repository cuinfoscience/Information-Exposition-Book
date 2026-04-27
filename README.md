# Information Exposition

[![Render and Publish](https://github.com/cuinfoscience/Information-Exposition-Book/actions/workflows/publish.yml/badge.svg)](https://github.com/cuinfoscience/Information-Exposition-Book/actions/workflows/publish.yml)

A Quarto textbook for **INFO 3402: Information Exposition** at the University of Colorado Boulder, Department of Information Science.

This book is a hands-on guide to communicating the findings of data analyses using Python. It pairs computational skills (pandas, matplotlib, seaborn, statsmodels) with communication skills (audience, narrative, visual clarity, uncertainty), chapter by chapter. The audience is undergraduates who have completed one or two semesters of programming and want to develop both their data fluency and their ability to tell clear, honest stories with charts.

**Author:** Brian C. Keegan, Ph.D.

## Who this is for

Undergraduates who can write basic Python — variables, loops, functions, imports — but have not yet worked with pandas, matplotlib, or statistical modeling. The book builds those skills from scratch with a strong emphasis on *communication*: not just producing a correct chart, but producing a chart that tells a clear and honest story to a real audience. Students who have taken an introductory data science or statistics course will find this book extends those foundations toward the practical work of explaining results.

## Building the book

### Prerequisites

- [Quarto 1.4+](https://quarto.org/docs/get-started/)
- Python 3.11+ (the [Anaconda](https://www.anaconda.com/download) distribution is recommended)
- Jupyter (`pip install jupyter`) — Quarto's Python engine needs it even though code blocks do not execute during rendering

### Commands

From the repo root:

```bash
# Interactive preview with live reload
quarto preview

# Render the full book to HTML
quarto render

# Render a single chapter
quarto render chapters/05-clarity.qmd
```

Output is written to `book/`. Open `book/index.html` in a browser to view the rendered site. The `book/` directory is gitignored — it is rebuilt locally on every render and published to the `gh-pages` branch by CI.

The book is configured with `execute.eval: false` in [_quarto.yml](_quarto.yml), so code blocks display as source but are not executed during render. This keeps the build fast and independent of the datasets described in the appendices, which are hosted separately. Students are expected to run the code themselves in Jupyter notebooks.

## Project structure

```
Information-Exposition-Book/
│
├── _quarto.yml                       # book configuration
├── index.qmd                         # preface
│
├── chapters/
│   ├── 01-loading.qmd                # Part I — Shaping Data
│   ├── 02-aggregating.qmd
│   ├── 03-combining.qmd
│   ├── 04-reshaping.qmd
│   ├── 05-clarity.qmd
│   ├── 06-histograms.qmd             # Part II — Distributions
│   ├── 07-catplots.qmd
│   ├── 08-audience.qmd
│   ├── 09-temporal-data.qmd          # Part III — Trends
│   ├── 10-time-series.qmd
│   ├── 11-uncertainty.qmd
│   ├── 12-scatterplots.qmd           # Part IV — Relationships
│   ├── 13-linear-models.qmd
│   └── 14-validity.qmd
│
├── appendices/
│   ├── datasets.qmd
│   └── setup.qmd
│
└── .github/workflows/publish.yml     # CI: renders + publishes to GitHub Pages
```

## Book contents

| Part | Chapters | Theme |
|------|----------|-------|
| **I — Shaping Data** | Loading, Aggregating, Combining, Reshaping, Clarity | Foundational pandas operations and the design principles behind clear charts |
| **II — Distributions** | Histograms, Categorical Plots, Audience | Visualizing the shape of data and writing for a real reader |
| **III — Trends** | Temporal Data, Time Series, Uncertainty | Working with time and communicating what we don't know |
| **IV — Relationships** | Scatterplots, Linear Models, Validity | Bivariate and multivariate relationships, and judging when a relationship is causal |
| **Appendices** | Datasets, Setup | Dataset documentation and Python environment setup |

## Contributing

Contributions are welcome — typo fixes, clearer explanations, additional exercises, better worked examples.

- **Errata and small fixes**: open an [issue](https://github.com/cuinfoscience/Information-Exposition-Book/issues) or a pull request.
- **Larger contributions**: open an issue first to coordinate scope before submitting a PR.

Style conventions:

- Cross-references use Quarto's `@sec-` syntax; section anchors follow the pattern `{#sec-filename-sectionname}`.
- Callouts use `.callout-tip` (advice), `.callout-warning` (pitfalls), and `.callout-note collapse="true"` (exercises with solutions).
- Code blocks specify the language: ` ```{python} `, ` ```{bash} `.
- Code blocks are non-executing (`eval: false` in [_quarto.yml](_quarto.yml)); show output explicitly when it matters for the narrative.

## CI

Every push to `main` triggers [.github/workflows/publish.yml](.github/workflows/publish.yml), which renders the book and publishes it to GitHub Pages via the `gh-pages` branch (`quarto-dev/quarto-actions/publish@v2`). Pull requests against `main` run a render-only job for validation but do not publish. The workflow can also be triggered manually from the Actions tab.

After the first successful run, GitHub Pages must be configured once: **Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch: `gh-pages` / `(root)`**.

## Rendered book

The latest build is published to <https://cuinfoscience.github.io/Information-Exposition-Book/>.

## License

Released under the [MIT License](LICENSE).

## Acknowledgments

This book was developed for INFO 3402: Information Exposition in the Department of Information Science at the University of Colorado Boulder. It draws on the work of many excellent textbooks and resources in data visualization and communication, including Jonathan Schwabish's *Better Data Visualizations*, Claus Wilke's *Fundamentals of Data Visualization*, and the pandas, matplotlib, and seaborn documentation communities. It has benefited from the questions, frustrations, and insights of many cohorts of INFO 3402 students.
