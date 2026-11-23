# dss-powersim

Simulation-Based Power Analysis: a guide to power analysis by simulation
for mixed effects models, in R, Python, and Stata, with one worked design
(participants rating songs of two genres) carried through all three (the
Stata page fits a reduced version of the model, for run time). Live at
https://iqss.github.io/dss-powersim/. Written 2023 by Steve
Worthington and Dan Yuan (IQSS), with feedback from Jinjie Liu and Noah
Greifer; moved from bookdown to Quarto on the `dss-theme` extension in
2026, every chunk on the three implementation pages executed and frozen.

## Build

`quarto preview` or `quarto render`. The executed chunks are frozen in
`_freeze/`; every push to `main` publishes the site to `gh-pages`
(`.github/workflows/publish.yml`), rendering from the freeze with no R,
Python, or Stata on the runner. With `freeze: true` a project render
never executes a chunk. To re-execute a page, render that page on its
own (for example `quarto render r.qmd`) and commit its refreshed freeze.
Re-executing a page needs:

- R with the packages in `renv.lock` (`renv::restore()`): the R page, the
  calculation on the Power Analysis page, and the tables on the Power of
  What? page.
- Python through uv (`uv sync`; `_environment` points Quarto at `.venv`):
  the Python page.
- Stata on the machine: the Stata page. Statamarkdown finds it and runs
  each chunk in batch, replaying the chunks before it; the `violinplot`
  needs the five SSC packages the page's first block installs.

## Contributing

MIT for code (`LICENSE`), CC BY 4.0 for the text and figures (`LICENSE-content`). Comments and suggestions through the Request help
button on every page.
