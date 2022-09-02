# Documentation for Juwels

Link for full user documentation: https://apps.fz-juelich.de/jsc/hps/juwels/index.html

### Login
Public keys are uploaded to Jülich HPC systems via the user portal JuDoor (https://judoor.fz-juelich.de/) for each system separately. Uploaded public keys need to be additionally restricted to allow access only from certain connection sources.

Link for detailed info: https://apps.fz-juelich.de/jsc/hps/juwels/access.html#ssh-login

### Current projects

The current project on Juwels:
* Climate projections with high-resolution Arctic Ocean (**chhb19** and **hhb19**). Consist of two sub-projects:
   - FESOM2 hindcast and projection simulations (i.e., EPICA 1/4.5km Arctic simulations) 
   - AWI-CM 3.1 climate setup/testing

* ESM Testprojekt (**esmtst**) - for testing of our codes.
* 2021240014 - nextGEMS’ Twin JUWELS (**pra127**) - for JUWELS BOOSTER.
  
### Python environment with pyfesom2

We will use **stacked conda environments**, so that we don't all have to install the same environments and use up all the inodes on /p/project/. We will set up a "master-environment" containing all the standard packages (pyfesom2, xarray, numpy, pandas, cartopy, matplotlib, etc). Everyone can then first activate this and then stack their respective personal environment on top.

To use stacked environments (a quick overview from Paul):

$ conda activate --stack <second_env>  # double minus

or automatically:

$ conda config --set auto_stack 1  # Or True, both are the same

So, what happens? Your PATH gets prepended twice, libraries are first loaded from the outermost (newest or last loaded) part of the stack. There might be odd quirks popping up if you have the exact same version of something in both levels of the stack! 

Link for detailed info: https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#nested-activation

### Jupyter
Juwels has JupyterLab installed, allowing to run jupyter from your browser (https://jupyter-jsc.fz-juelich.de/hub/home). This is the best way to work with jupyter notebooks on Juwels.

Link for detailed info: https://docs.jupyter-jsc.fz-juelich.de/github/FZJ-JSC/jupyter-jsc-notebooks/blob/documentation/index.ipynb

#### Installing jupyter kernel from conda environment
In order to run your conda environments in JupyterLab, they first have to be installed as a kernel.

Follow the steps in this description to get a working Jupyter Kernel from your conda environment: https://docs.jupyter-jsc.fz-juelich.de/github/FZJ-JSC/jupyter-jsc-notebooks/blob/documentation/03-HowTos/Create_JupyterKernel_conda.ipynb

We will add information on how to install a kernel from a stacked environment once the "master-environment" is ready.

### Best practice for data storage

There are several different file systems available from juwels, each with a different purpose and different limitations.  

Link for detailed info: https://apps.fz-juelich.de/jsc/hps/juwels/environment.html#available-file-systems

The file systems available for us are:
- $HOME  
  - 20GB/80K inodes limit per person (increased from 2GB, so this is great!)
  - personal directory
  - use for personal files, scripts, software, SSH-keys etc.
- $PROJECT  
  - 10TiB/3M inodes limit
  - use for shared data, project related source code, binaries, etc.
- $SCRATCH **not backed up**
  - 200TiB/5M inodes limit
  - use for temporary data, model output etc. 
  - easy/fast access -> postprocessing/analysis from here

- $LARGEDATA  
  - 600TiB/3M inodes limit
  - use for storing large amounts of data 
  - limited/slow access -> **no postprocessing/analysis** from here
  
- $ARCHIVE  
  - 600TiB/100K inodes limit
  - magnet tape for archiving data

All quotas are also listed here: https://apps.fz-juelich.de/jsc/hps/juwels/faq.html?highlight=quota#list-usage

Our current usage status etc. can be found in the user portal JuDoor (https://judoor.fz-juelich.de/)
