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

Run the Miniconda3 installation script in batch mode.
```
bash Miniconda3-latest-Linux-x86_64.sh -b -f
```

Then, add the following line at the bottom of your .bashrc file. **Important, replace xdtr99 with your Expanse username!**
```
source /home/xdtr99/miniconda3/etc/profile.d/conda.sh
```

You can use the `nano` editor to edit your .bashrc file, e.g. `nano .bashrc`.

To make the changes to your .bashrc take effect, run the following command.
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

Then, create a Conda environment that contains specific versions of all the packages needed to reproduce the results of this study. Note, the `&` at the end. This will run the command in the background. The nohup command will keep the installation going, even if you logout or get disconnected. **Note, this step may run for an hour a longer.**
```
nohup conda env create -f notebooks-sharing/environment.yml > conda-notebook-env-install.log &
```

Next, check if the `notebooks-sharing` environment has been created.
```
conda env list
```

You should see the following output:
```
# conda environments:
#
base                  *  /home/xdtr99/miniconda3
notebooks-sharing        /home/xdtr99/miniconda3/envs/notebooks-sharing
```

If you do not see the expected output, check the `conda-notebook-env-install.log` file for error messages.

#### What should I do if any of these steps fail?
First, you can post any problem in the Slack channel and we'll work with you to try to fix it. We still have a few days to fix any issues. The hands-on session on Thursday will use this setup.

If all fails, we have a backup solution. Add the following line at the bottom of your .bashrc file to use a preinstalled conda environment.
```
source /home/xdtr99/miniconda3/etc/profile.d/conda.sh
```

You can use the `nano` editor to edit your .bashrc file, e.g. `nano .bashrc`.

To make the changes to your .bashrc take effect, run the following command.
```
source ~/.bashrc
```

### Run the Jupyter Notebooks in an Expanse Terminal

Use the galyleo script to launch Jupyter on the Expanse command line. First, set the path to the galyleo script.

```
export PATH="/cm/shared/apps/sdsc/galyleo:${PATH}"
```

Run the galyleo script to launch Jupyter. We already specified your Expanse project allocation account number (sds184) with the `--account` option. In general, you can look up your allocation information from the [Expanse Portal Dashboad](https://portal.expanse.sdsc.edu) under the Clusters->Allocation and Usage Information tab.

```
galyleo.sh launch --account sds184 --partition 'shared' --cpus-per-task 1 --memory-per-node 4 --time-limit 00:30:00 --jupyter 'lab' --notebook-dir "/home/${USER}" --conda-env 'notebooks-sharing'
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



