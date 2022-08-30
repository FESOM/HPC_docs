# Documentation for Juwels

### Login
Public keys are uploaded to Jülich HPC systems via the user portal JuDoor (https://judoor.fz-juelich.de/) for each system separately. Uploaded public keys need to be additionally restricted to allow access only from certain connection sources.

all the detailed info: https://apps.fz-juelich.de/jsc/hps/juwels/access.html#ssh-login

### Current projects
- EPICA - high resolution arctic simulations
  - Qiang Wang
  - Nikolay Koldunov
  - Vasco Mueller
  - Xinyue Li
  
- AWI-CM3 setup and testing
  - Jan Streffing
### Python environment with pyfesom2
We will use **stacked conda environments**, so that we don't all have to install the same environments and use up all the inodes on /p/project/. We will set up a "master-environment" containing all the standard packages (pyfesom2, xarray, numpy, pandas, cartopy, matplotlib, etc). Everyone can then first activate this and then stack their respective personal environment on top.

To use stacked environments (a quick overview from Paul):

$ conda activate --stack <second_env>  # double minus

or automatically:

$ conda config --set auto_stack 1  # Or True, both are the same

So, what happens? Your PATH gets prepended twice, libraries are first loaded from the outermost (newest or last loaded) part of the stack. There might be odd quirks popping up if you have the exact same version of something in both levels of the stack! 

Docu link: https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#nested-activation

### Jupyter
Juwels has JupyterLab installed, allowing to run jupyter from your browser (https://jupyter-jsc.fz-juelich.de/hub/home). This is the best way to work with jupyter notebooks on Juwels.

You can find the full documentation here: https://docs.jupyter-jsc.fz-juelich.de/github/FZJ-JSC/jupyter-jsc-notebooks/blob/documentation/index.ipynb

#### Installing jupyter kernel from conda environment
In order to run your conda environments in JupyterLab, they first have to be installed as a kernel.

Follow the steps in this description to get a working Jupyter Kernel from your conda environment: https://docs.jupyter-jsc.fz-juelich.de/github/FZJ-JSC/jupyter-jsc-notebooks/blob/documentation/03-HowTos/Create_JupyterKernel_conda.ipynb

We will add information on how to install a kernel from a stacked environment once the "master-environment" is ready.
