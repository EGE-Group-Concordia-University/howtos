# Setup a user Kernel
It is possible to setup your own Kernel in the JupyerHub servers of our laboratory. This allows you to install libraries without having administrator privileges and to setup virtual environments without interfering with other users and kernels.

The main steps to follow are (see details below):
1. Setup a virtual environment using `/opt/conda/bin/python3 -m venv <my-env>`
2. Add the `ipykernel` library to the virtual environment
3. Setup the virtual environment as a kernel with `python -m ipykernel install --user –name=<my_kernel>`

All the following steps must be executed inside a terminal open from your JupyterHub server.

## Setup your virtual environment
Create a folder `venv` in which you will setup your virtual environment:
```
mkdir venv
```
This folder can be anywhere. But as the virtual environment you plan to setup is in general not specific for a given project, but will be used in various projects, a good place to create this folder is in your home folder.

Inside the `venv` folder create your virtual environment like so:
```
/opt/conda/bin/python3 -m venv my_env
```
where `my_env` is the name of your environment you wish to create.

Note: use `/opt/conda/bin/python3` and not `pyhton3` to make sure to use the correct `python` (the one used by the JupyterHub server).

This will create a folder `my_env` within the folder `venv`.

Activate your environment like so:
```
source my_env/bin/activate
```
To check if everything works well and at same time get latest version of `pip` run:
```
pip install --upgrade pip
```
This should upgrade `pip` in your environment, or confirm that it is at the latest version.

Install all libraries you want to add to your environment. In this example we add the library `kafka-python`:
```
python3 -m pip install kafka-python
```
You can install as many libraries as desired and you can add later more libraries as needed.

## Setup your virtual environment as a JupyterHub Kernel
In order to become a Kernel for JupyterHub, the following library needs to be installed in the virtual environment (make sure your virtual environmetn is activated):
```
python3 -m pip install ipykernel 
```
The virtual environment is transformed into a JupyterHub kernel by running (make sure your virtual environmetn is activated):
```
python -m ipykernel install --user --name=my_kernel
```
where any name for the Kernel can be choosen (here we used `my_kernel`)

At this point the Kernel should show up in your JupyterHub account together with the other defined kernels. You may have to stop and restart your server from File>Hub Control Panel.

You can verify that the Kernel is correctly recognized by the JupyterHub server bu running
```
jupyter kernelspec list
```
which will show something like this:
```
Available kernels:
  ...
  my_kernel    /home/wuthrich/.local/share/jupyter/kernels/my_kernel
  ...
```

## Remove your Kernel
To remove your Kernel run
```
jupyter kernelspec remove my_test_kernel
```
This only removes the link between your virtual environment and JupyterHub. 
If you want to further to remove your virtual environment you will have to remove the folder `my_env`.
