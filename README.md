# sphinx-plantuml-github-pages-template

## About

A set of template scripts to develop document with [Sphinx](https://www.sphinx-doc.org/) and [PlantUML](https://plantuml.com/) and then publish it to [GitHub Pages](https://pages.github.com/) using [GitHub Actions](https://github.com/features/actions).

Folder structure and config file were generated with `sphinx-quickstart` command described in [here](https://www.sphinx-doc.org/en/master/usage/quickstart.html).

## Getting Started

### Prerequisites

- For Local Development

  - pyenv (python 3.9)
    - <https://github.com/pyenv/pyenv>
    - <https://github.com/pyenv-win/pyenv-win>
  - pipenv
    - <https://pipenv.pypa.io/en/latest/>
  - PlantUML environment
    - <https://plantuml.com/starting>
    - Graphviz
      - <https://graphviz.org/>
    - Java Runtime

- For UML diagram writing

  - Recommend to use VSCode + PlantUML plugin.

- To Publish Page to GitHub Pages with GitHub Actions
  - A Repo with GitHub Pages enabled with GitHub Actions Trigger
  - A GitHub credential which includes workflow scope

### Folder Structure

```txt
sphinx-plantuml-github-pages-template
├ .github
│  └ workflows  # Folder for github actions definition
│     └ github-actions-sphinx.yml
└　docs
  ├ build       # Folder for build document
  ├ source      # Folder for document source
  ├ conf.py     # Configuration file for the Sphinx documentation builder
  └ index.rst   # Top level document contains Table Of Contents (TOC) information

```

### Start Documentation

```sh
# install dependencies
$ cd docs && pipenv install

# auto build and reload
# can check latest document on http://127.0.0.1:8000 with browser
$ cd docs && pipenv run sphinx-autobuild source build/html
```

### Publish Document

Document push to the origin will trigger workflow described below.

Published document can be found at <https://ryotaimc.github.io/sphinx-plantuml-github-pages-template/>

![flow](./README/flow.png)

```plantuml
@startuml
participant Local as l
participant GitHub as g
participant GitHub_Actions as ga
participant GitHub_Pages as gp
l->g: push
g->ga: trigger
activate g
ga->g: pull
activate ga
g-->ga: checkout
ga->ga: build
ga->gp: publish
@enduml
```
