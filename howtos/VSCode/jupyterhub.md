# JupyterHub in VSCode

## Adjust working directory of Jupyter Notebooks
In VSCode JupyterHub extension, the working directory is not the directory in which the notebook is stored, as it is the case in JupyterLab.
This can be changed by adding the following entry to user `settings.json` file (open it with [Ctrl]+[Shift]+[P] "Preferences: Open User Settings (JSON)"):
```
"jupyter.runStartupCommands": [
    "import os, IPython\nos.chdir(os.path.dirname(IPython.extract_module_locals()[1]['__vsc_ipynb_file__']))"],
```
