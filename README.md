# Writing and Sharing Computational Analyses in Jupyter Notebooks

** UNDER CONSTRUCTION **

## How to run the Jupyter Notebook Examples

** Prerequisites **

You need an up-to-date version on miniconda3 and git. 

If you do not have miniconda3 and git installed, follow the directions in the ["Ten Simple Steps to setup Python 3 and Jupyter Lab" guide](https://github.com/pwrose/python-jupyter).

**1. Fork this project**

A [fork](https://help.github.com/en/articles/fork-a-repo) is a copy of a repository in your GitHub account. Forking a repository allows you to freely experiment with changes without affecting the original project.

In the top-right corner of this GitHub page, click ```Fork```.

Then, download all materials to your laptop by cloning your copy of the repository, where ```your-user-name``` is your GitHub user name. To clone the repository from a Terminal window, run:

```
git clone https://github.com/your-user-name/notebooks-sharing.git
cd notebooks-sharing
```

**2. Create a conda environment**

The file `environment.yml` specifies the Python version and all packages required by the tutorial. 
```
conda env create -f environment.yml
```

Activate the conda environment
```
conda activate notebooks-sharing
```

**3. Launch Jupyter Lab**
```
jupyter lab
```

To shutdown Jupyter Lab, go to ```File -> Shut Down```

**4. Deactivate the conda environment
```
conda deactivate
```

### Removing the conda environment

If you want to remove the conda environment, type
```
conda env remove -n notebooks-sharing
```



