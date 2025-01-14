# anat-processing-book

Notebook that describes processing of anatomical data for the [Courtois-Neuromod Project](https://www.cneuromod.ca/). 

To visualize the notebook click [here](https://courtois-neuromod.github.io/anat-processing-book/).

## GitHub Action for automatic [Jupyter-Book GitHub page](https://courtois-neuromod.github.io/anat-processing-book/index.html) builds

A [GitHub Action](https://github.com/courtois-neuromod/anat-processing-book/blob/main/.github/workflows/main.yml) is responsible for bulding jupyter-book from the `source` directory, then pushing built html files to the gh-pages branch. 

**1. Please ensure that the notebooks under the `source` directory are pushed to the `main` with the outputs saved.**

* GitHub actions will not re-execute the notebooks, only the html outputs will be built based on what's saved in the notebooks (e.g. interactive figures). 

**2. Please be careful with pushing changes to the following lines of the `source/_config.yml` if [`requirements.txt`](https://github.com/courtois-neuromod/anat-processing-book/blob/main/requirements.txt):**

```yaml
execute:
  execute_notebooks: 'off'
```

* Setting this to `auto` or `on` will enforce book build to re-execute the notebooks during GitHub Actions build, which may fail if there are dependencies additional to those listed by `requirements.txt`. 

## Build the Notebook locally

Install miniconda

Create and activate virtual environment:
~~~
conda create -n notebook_docs pip
conda activate notebook_docs
~~~

Install required packages
~~~
pip install -r requirements.txt
~~~

Build the notebook
~~~
jupyter-book build source/ --path-output _build
~~~
