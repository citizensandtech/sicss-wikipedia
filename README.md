# sicss-wikipedia

Preparing the notebooks in R/Python for teaching how to use the 
Wikimedia/MediaWiki APIs at SICSS events as part of the 
[Wikimedia at Summer Institutes in Computational Social Sciences](https://meta.wikimedia.org/wiki/Research:Wikimedia_at_Summer_Institutes_in_Computational_Social_Science)
project.


## Building the pages

This project uses [Quarto](https://quarto.org/) and the [Babelquarto](https://docs.ropensci.org/babelquarto/) R packages to render out a multi-lingual website.

As of 2026-05-15, the actual rendering should still happen using [Bastian's branch](https://github.com/gedankenstuecke/babelquarto/tree/20260513-ipynb-support), as it adds support for rendering multilingual Jupyter notebooks too.


### Step-by-step setup and building:

To get started, get the corresponding two repos checked out:

``
git clone git@github.com:gedankenstuecke/babelquarto.git
cd babelquarto; git checkout 20260513-ipynb-support; cd ..
git clone git@github.com:citizensandtech/sicss-wikipedia.git
cd sicss-wikipedia
``

Assuming you have an R environment that includes `devtools`, you can 
now build the pages by opening thean R shell from the `sicss-wikipedia` folder and run:

```
devtools::load_all("../babelquarto")
render_website(site_url= "https://citizensandtech.github.io/sicss-wikipedia")
```

This creates the final website in the `_site` directory.


## Adding new content:

You can either create `*.qmd` pages for R code and edit those using your R-environment of choice,
or create Jupyter notebooks.

By default, a Jupyter notebook are rendered out to HTML *as is*, without re-running any cells, while Quarto markdown files will be fully executed.

For either files, make sure that a `*.fr.qmd` or `*.fr.ipynb` version exists for the French translation and cross-linking.

Once the files exist, they can be added to the menu bar by adding them to the `navbar` key in `_quarto.yml`


## Deployment

The live pages are deployed from the `gh-pages` branch of this repository.
The build using `babelquarto` happens automatically from the `main` branch via a GitHub action.
