# Supporting Materials for Clustering and Visualising Documents using Word Embeddings
This GitHub repository is intended to provide supporting materials for the tutorial [published on Programming Historian](https://doi.org/10.46430/phen0111). The contents can be divided up into several parts:

### Setup

There are three options connected to the setting up of Python for this tutorial:

1. **Direct Installation**: if you are installing the required Python libraries directly (e.g. `pip install`) then you can do so using the [`requirements.txt`](requirements.txt) file as follows:
    `pip install -r requirements.txt`. This will install the latest version of each library named in the requirements file. So, over longer periods of time, changes to these libraries may eventually result in errors because the interface/functions used have change.
2. **Google Colab**: this has been set up by Programming Historian so that the environment is created automatically for you and so is the easiest way to run this tutorial. It also draws on `requirements.txt` but there is nothing for you to do as Google Colab will install the libraries automatically.
3. **Docker**: this approach ensures that you are *always* running the version of Python (and the associated required libraries) that were used in developing this tutorial. So this approach will work for as long as Docker continues to exist as a (mostly free) software platform. Details for running the Docker image can be [found here](./docker/README.md). If you know what you're doing with Docker already: `docker pull jreades/ph-tutorial:latest`.

### Code

There are two Jupyter Notebooks that you can run interactively:

1. [Clustering_Word_Embeddings.ipynb](Clustering_Word_Embeddings.ipynb): the main tutorial. This takes you through downloading the data, installing the one library that is not available via `pip`, and then performing the analysis [presented in the tutorial](https://doi.org/10.46430/phen0111).
2. [Comparison_to_PCA.ipynb](Comparison_to_PCA.ipynb): this separate notebook informs the brief section about the limitations of Principal Components Analysis (PCA) on 'non-linear' data used in [another tutorial](https://programminghistorian.org/en/lessons/clustering-with-scikit-learn-in-python). This code should run independently of anything in the main tutorial as we're working with a different data set (downloaded automatically for you in the tutorial).

### Other

There is also a [Supplementary Materials](Supplementary_Materials.md) file -- technically, this relates to an earlier version of the tutorial in which different EThOS data was used; however, I've left it here as it's useful additional context for the results reported in the newer tutorial.

