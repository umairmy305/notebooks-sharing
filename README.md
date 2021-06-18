# Writing and Sharing Computational Analyses in Jupyter Notebooks

This repository demonstrates the ["Ten Simple Rules for Reproducible Research in Jupyter Notebook"](https://arxiv.org/abs/1810.08055) rules for a simple machine learning problem and is based on this ["ten-rules-jupyter"](https://github.com/jupyter-guide/ten-rules-jupyter) GitHub repository. It was developed for the [CIML Summer Institute 2021](https://github.com/ciml-org/ciml-summer-institute-2021).

The workflow is broken down into four independent steps, with a notebook for each step
* Create a dataset [1-CreateDataset.ipynb](notebooks/1-CreateDataset.ipynb) 
* Calculate features [2-CalculateFeatures.ipynb](notebooks/2-CalculateFeatures.ipynb) 
* Fit a model [3-FitModel.ipynb](notebooks/3-FitModel.ipynb) 
* Make a prediction [4-Predict.ipynb](notebooks/4-Predict.ipynb) 

## Run the Jupyter Notebooks in your Web Browser

The [MyBinder.org](https://mybinder.org/) service let's you run the notebooks in this repository from your web browser by simply clicking on the launch link (the launch may take a couple of minutes). MyBinder launch links can be created for an entire repository or for a specific notebook. 

Your task is to insert launch links for both cases.

**Insert a MyBinder.org launch link for this repository.**

*launch link goes here*
 
**Insert a MyBinder.org launch link for the [4-Predict.ipynb](notebooks/4-Predict.ipynb) notebook.**

*launch link goes here*


## Setup for Expanse
Login with your Expanse username (xdtrXX). Note, this username is different from your XSEDE username (trainXX).

```
ssh <username>@login.expanse.sdsc.edu
```

#### Install Miniconda3 for Linux-x86_64
Download the Minconda3 installation script.

```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
```
Run the Miniconda3 installation script.
```
bash Miniconda3-latest-Linux-x86_64.sh
```
Follow the prompts on the installer screens. Answer **yes** to the prompts and accept the defaults.

The installer will modify your .bashrc file. To make the changes take effect, run the following command.
```
source ~/.bashrc
```

Test the installation.
```
conda list
```
A list of installed packages appears if it has been installed correctly.


#### Create a Conda Environment for the notebooks-sharing Repository
First, create a local copy of the training repository by cloning it with git.
```
git clone https://github.com/sdsc-hpc-training-org/notebooks-sharing.git
```

Then, create a Conda environment that contains specific versions of all the packages needed to reproduce the results of this study. Note, the `&` at the end. This will run the command in the background.
```
conda env create -f notebooks-sharing/environment.yml &
```
Finally, disown the background process so it continues even if your terminal window times out.
```
disown %1
```

### Run the Jupyter Notebooks in an Expanse Terminal

Use the galyleo script to launch Jupyter on the Expanse command line. First, set the path to the galyleo script.

```
export PATH="/cm/shared/apps/sdsc/galyleo:${PATH}"
```

Run the galyleo script to launch Jupyter. We already specified your Expanse project allocation account number (sds184) with the `--account` option. In general, you can look up your allocation information from the [Expanse Portal Dashboad](https://portal.expanse.sdsc.edu) under the Clusters->Allocation and Usage Information tab.

```
galyleo.sh launch --account sds184 --partition 'shared' --cpus-per-task 1 --memory-per-node 4 --time-limit 00:30:00 --jupyter 'lab' --notebook-dir "/home/${USER}" --conda-env 'notebooks-sharing' --quiet
```

After you run this command, a URL is displayed. Copy this URL and paste it into a web browser to launch your interactive session.

### Run the Jupyter Notebooks from the Expanse Portal

To run the notebooks on the Expanse portal, follow these [steps](docs/Expanse_portal.md).

### Run the Jupyter Notebooks on your own Computer

**Prerequisites**

You need an up-to-date version of miniconda3 and git. 

If you do not have miniconda3 installed, follow the directions in the "Eight Simple Steps to setup Python 3 and Jupyter Lab" [guide](https://github.com/pwrose/python-jupyter#eight-simple-steps-to-setup-python-3-and-jupyter-lab).

Once miniconda3 is installed, you can install git with the following command:
```
conda install -c conda-forge git
```
 
**1. Fork this project**

A [fork](https://help.github.com/en/articles/fork-a-repo) is a copy of a repository in your GitHub account. Forking a repository allows you to freely experiment with changes without affecting the original project.

In the top-right corner of this GitHub page, click ```Fork```.

Then, download all materials to your laptop by cloning your copy of the repository, where ```your-github-username``` is your GitHub user name. To clone the repository from a Terminal window, run:

```
git clone https://github.com/your-github-username/notebooks-sharing.git
cd notebooks-sharing
```

**2. Create a conda environment**

The file `environment.yml` specifies the Python version and all packages required by the tutorial. 
```
conda env create -f environment.yml
```

```
conda activate notebooks-sharing
```

**3. Launch Jupyter Lab**
```
jupyter lab
```

To shutdown Jupyter Lab, go to `File -> Shut Down`

**4. Deactivate the conda environment**

```
conda deactivate
```

### Removing the conda environment

To remove the conda environment, type
```
conda env remove -n notebooks-sharing
```



