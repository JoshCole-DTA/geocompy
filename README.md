# geocompy

[![Render](https://github.com/geocompr/py/actions/workflows/main.yaml/badge.svg)](https://github.com/geocompr/py/actions/workflows/main.yaml)
<!-- [![Binder](http://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/geocompr/py/main?urlpath=lab/tree/ipynb) -->
[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://github.com/codespaces/new?hide_repo_select=true&ref=main&repo=447558863)

<https://geocompr.github.io/py/>

Broadly, the book can be reproduced after following three steps:

1. Install Quarto https://quarto.org/docs/get-started/
2. Install Jupyter, RStudio or VS Code
3. Install the Python dependencies with `miniconda3` (recommended) or Docker

Detailed instructions are provided below.

<!-- ## Reproduce the book in Binder

To reproduce this book you can simply click on the link below to see the code running in your web browser (see details of how this works at [mybinder.org](https://mybinder.org/)):

[![Binder](http://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/geocompr/py/main?urlpath=lab/tree/ipynb)
 -->

## Reproduce the book with GitHub Codespaces

GitHub Codespaces is a system that allows you to run code in GitHub repositories on remote machines.
Like Google Collab and Binder, Codespaces minimise set-up costs to almost zero by providing integrated development environments in your browser, without the need to install various dependencies described in the sections below.
A unique advantage of codespaces is its integration with GitHub, allowing you to make changes, see how they improve the rendered content, and then push the changes back to your own fork of the book's repo.

To run the book in Codespaces, click on the link below.

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://github.com/codespaces/new?hide_repo_select=true&ref=main&repo=447558863)

You should see something like this, the result of running all the code in the book by opening the terminal (e.g. with the command Ctrl+J) and entering the following command:

```
quarto preview
```

![](https://user-images.githubusercontent.com/1825120/202933280-e313c076-f188-4efd-9de1-5625eb169045.png)

If you have any issues related to running the code in Codespaces let us know in the [issue tracker](https://github.com/geocompr/py/issues/114).

## Reproduce the book with Docker (devcontainer)

For many people the next quickest way to reproduce the book will be in a Docker container running on your local computer.
To do this from within VS Code (recommended), you can

1. Install Microsoft's official [Dev Container](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extension
2. Open the folder containing the repo in VS Code and click on the 'Reopen in container' button that should appear, as shown below (you need to have Docker installed on your computer for this to work)

![](https://user-images.githubusercontent.com/1825120/202933928-eb6de086-f9a5-43cd-9932-e6ec84746d45.png)

Edit the code in the containerised instance of VS Code that will appear 🎉

## Reproduce the book with mamba

To reproduce the book with the mamba package manager, first install [miniforge](https://github.com/conda-forge/miniforge#mambaforge).

Install mamba with the following commands on Unix alike plateforms:

```bash
curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Mambaforge-$(uname)-$(uname -m).sh"
bash Mambaforge-$(uname)-$(uname -m).sh
```
After answering the questions, install dependencies with the following command:

```bash
mamba env create -f environment.yml
```

Activate the environment as follows:

```bash
mamba activate geocompy
```

and reproduce the book (requires quarto to be installed):

```bash
quarto preview
```

## Reproduce the book with conda installation

### Installation on Windows

* Install [miniconda](https://docs.conda.io/en/latest/miniconda.html) either by:
  - Downloading and running the .exe link manually, or
  - With the [command](https://community.chocolatey.org/packages/miniconda3) `choco install miniconda3` from a PowerShell terminal after installing [Chocolatey](https://chocolatey.org/install)
* Open the Anaconda Prompt (or a fresh PowerShell terminal after running the command [`conda init powershell`](https://github.com/conda/conda/issues/8428#issuecomment-474867193) from the Anaconda prompt), navigate to the above-mentioned working directory, and then run:

### Installation on Mac/Linux

Install conda, e.g. with the following commands in a Linux terminal:

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-py39_4.12.0-Linux-x86_64.sh
chmod +x Miniconda3-py39_4.12.0-Linux-x86_64.sh
./Miniconda3-py39_4.12.0-Linux-x86_64.sh
```
You should see prompts like this:

```
Please answer 'yes' or 'no':'
>>> yes

Miniconda3 will now be installed into this location:
/home/robin/miniconda3

  - Press ENTER to confirm the location
  - Press CTRL-C to abort the installation
  - Or specify a different location below
```

### Create and activate conda environment

After installing conda you should be able to run the `conda create env` command above from bash to install the dependencies.

```sh
 # Warning may take several (10+) minutes to install the dependencies:
conda env create -f environment.yml
```

Activate the new environment with

```sh
conda activate geocompy # the default name of the environment
```

### Serving a local version of the book with quarto

Reproduce a live preview of the book with the following command, which reqires that you have installed [quarto](https://quarto.org/):

```sh
quarto preview # generate live preview of the book
```

### Reproducing chapters with jupyter

* Open the Jupyter Notebook of any of chapters using a command such as:

```sh
cd ipynb
# jupyter notebook . # open a notebook showing all chapters
jupyter notebook 02-spatial-data.ipynb
```

You should see something like this: 

![](https://user-images.githubusercontent.com/1825120/176920562-d2e7f9af-84b4-4352-8a50-9d9946084c66.png)

See documentation on running and developing Python code in a Jupyter notebook at [docs.jupyter.org](https://docs.jupyter.org/en/latest/).

### Updating packages/environments with conda

<details>

Update all packages to the latest versions as follows:

```sh
conda update --all
```


You can also install individual packages with:

```sh
conda install jupyter # for example
```

or

```sh
conda install -c conda-forge topojson # from the conda-forge channel
```

If you ever want to remove the environment, which is called `geocompy` by default, you can run the following command:

```sh
conda env remove -n geocompy
```

</details>

## Installing packages with pip

<details>

For Linux, use your preferred package manager to install the packages used in the book (`geopandas`, `rasterio`, etc.) as specified in each chapter, as well as the Jupyter Notebook interface. For example, using `pip` to install the Jupyter Notebook package is as follows:

```sh

pip install jupyter-book
```

</details>

## Updating the .py and .ipynb files

The Python scripts and IPython notebook files stored in the [code](code) and [ipynb](ipynb) folders are generated from the .qmd files.
To regenerate them, you can use the following commands, to generate .ipynb and .py files for local versions of Chapter 2, for example:

```bash
quarto convert 02-spatial-data.qmd # generate .ipynb file
jupytext --to py *.ipynb # generate .py files .ipynb files
```

Do this for all chapters with the following bash script in the repo:

```bash
./convert.sh
```

## Updating .py and .ipynb files with GitHub Actions

We have set-up a GitHub Action to do this automatically: every commit message that contains the text string 'convert' will create and push updated .ipynb and .py files.

## Executing the .py and .ipynb files

Running the code chunks in the .qmd files in an IDE such as VSCode or directly with quarto is the main way code in this book is designed to be run interactively, but you can also execute the .py and .ipynb files directly.
To run the code for chapter 2, for example, you can run one of the following commands from your system shell:

```bash
python code/chapters/02-spatial-data.py # currently requires manual intervention to complete, see #71
ipython ipynb/02-spatial-data.ipynb # currently requires manual intervention to complete, see #71
bash ./run-code.sh # run all .python files
```

<!-- ## Reproduce the book in a Docker container with VSCode IDE -->

<!-- Todo: help wanted -->

<!-- ## Reproduce the book in a Docker container

Note: experimental.

```
docker run -it -p 8888:8888 -v $(pwd):/root geocompr/geocompr:mamba
jupyter 
```

## Reproduce the book in a Docker container with RStudio IDE

```bash
docker pull geocompr/geocompr:python
# Remove the --rm below for a persistent image
docker run --rm -d -p 8784:8787 -e DISABLE_AUTH=TRUE --name geocompy \
  -v $(pwd):/home/rstudio/pytest geocompr/geocompr:python
firefox localhost:8784 # or your browser of choice
# docker kill geocompy # stop the image
```

After opening the relevant project running `quarto preview` in the system shell in browser-based IDE opened by the command above, you should see something like this where you can run code and even modify the book and see changes with the previou command.

![](https://user-images.githubusercontent.com/1825120/156414301-bfe622c5-1290-4f85-8a21-08d2a6d77df1.png) -->


