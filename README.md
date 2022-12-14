[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/KAUST-Academy/introduction-to-python/HEAD)

# Introduction to Python

Course materials for introductory workshops on Python targeting data scientists and AI practioners. Participants are encouraged to download and install one of the Python distributions from [Anaconda](https://anaconda.org/), either the full [Anaconda](https://www.anaconda.com/products/distribution) distribution or the [Miniconda](https://docs.conda.io/en/latest/miniconda.html) distribution. 

## Core data science libraries

* [Jupyter](https://jupyter.org/)
* [NumPy](https://numpy.org/)
* [SciPy](https://scipy.org/)
* [Pandas](https://pandas.pydata.org/)
* [Matplotlib](https://matplotlib.org/)

## Data visualization libraries

* [Bokeh](https://bokeh.org/)
* [HoloViews](https://holoviews.org/)
* [GeoViews](https://geoviews.org/)
* [DataShader](https://datashader.org/)
* [Panel](https://panel.holoviz.org/)
* [PyViz](https://pyviz.org/index.html)

## Machine learning libraries

* [Scikit-Learn](https://scikit-learn.org/stable/index.html)
* [Dask](https://www.dask.org/)
* [Rapids](https://rapids.ai/)

## Deep learning libraries

* [PyTorch](https://pytorch.org/)
* [PyTorch Lightning](https://www.pytorchlightning.ai/)
* [TensorFlow](https://www.tensorflow.org/)
* [Keras](https://keras.io/)

## Lesson materials

* [Programming with Python](http://swcarpentry.github.io/python-novice-inflammation)
* [Plotting and Programming with Python](http://swcarpentry.github.io/python-novice-gapminder)
* [Data Analysis and Visualization with Python](https://datacarpentry.org/python-ecology-lesson/)

## Project organization

Project organization is based on ideas from [_Good Enough Practices for Scientific Computing_](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005510).

1. Put each project in its own directory, which is named after the project.
2. Put external scripts or compiled programs in the `bin` directory.
3. Put raw data and metadata in a `data` directory.
4. Put text documents associated with the project in the `doc` directory.
5. Put all Docker related files in the `docker` directory.
6. Install the Conda environment into an `env` directory. 
7. Put all notebooks in the `notebooks` directory.
8. Put files generated during cleanup and analysis in a `results` directory.
9. Put project source code in the `src` directory.
10. Name all files to reflect their content or function.

## Using Conda

### Creating the Conda environment

After adding any necessary dependencies for your project to the Conda `environment.yml` file 
(or the `requirements.txt` file), you can create the environment in a sub-directory of your 
project directory by running the following command.

```bash
ENV_PREFIX=$PWD/env
conda env create --prefix $ENV_PREFIX --file environment.yml --force
```

Once the new environment has been created you can activate the environment with the following 
command.

```bash
conda activate $ENV_PREFIX
```

Note that the `ENV_PREFIX` directory is *not* under version control as it can always be re-created as 
necessary.

For your convenience these commands have been combined in a shell script `./bin/create-conda-env.sh`. 
Running the shell script will create the Conda environment, activate the Conda environment, and build 
JupyterLab with any additional extensions. The script should be run from the project root directory as 
follows. 

```bash
./bin/create-conda-env.sh
```

### Listing the full contents of the Conda environment

The list of explicit dependencies for the project are listed in the `environment.yml` file. To see 
the full lost of packages installed into the environment run the following command.

```bash
conda list --prefix $ENV_PREFIX
```

### Updating the Conda environment

If you add (remove) dependencies to (from) the `environment.yml` file or the `requirements.txt` file 
after the environment has already been created, then you can re-create the environment with the 
following command.

```bash
$ conda env create --prefix $ENV_PREFIX --file environment.yml --force
```

If you have added any JupyterLab extensions or made any other changes to the `postBuild` script, then you 
should re-create the entire Conda environment by re-running the `bin/create-conda-env.sh` scipt as follows.

```bash
./bin/create-conda-env.sh
```

## Using Docker

In order to build Docker images for your project and run containers you will need to install 
[Docker](https://docs.docker.com/install/) and [Docker Compose](https://docs.docker.com/compose/install/).

Detailed instructions for using Docker to build and image and launch containers can be found in 
the `docker/README.md`.
