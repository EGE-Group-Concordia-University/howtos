# Virtual environments with Python

Python virtual environments allow to address two issues
1)	It allows, on a project base, to install the python libraries required for the project and this way avoids issues with conflicting versions of libraries 
2)	It allows not privileged users (without admin privileges) to install the required libraries for their work

## Prerequisites
The required software packages / libraries can be installed like so (required amdin privilege)
```
sudo apt install python3 python3-venv python3-pip
```

## Setting up a virtual environment in your account

### Setup folder for your virtual environment
In your home folder create a folder to hold your virtual environments (in our case we make the folder `venv`)
```
mkdir venv
```
This folder will contain all your virtual environments you may setup in future. 

It is strongly recommended to have one virtual environment per project.

Note: 
In principle the folder for your virtual environment could be anywhere on your machine. However, on servers from our group it is required to have it in your home folder (as otherwise it will jam the Owncloud sync process) 

### Create python virtual environment
In the virtual environment folder created above (`~/venv`) run:
```
cd ~/venv	
python3 -m venv myenv
```
Replace `myenv` by any suitable name for your project of your choice (for example if your project is on machine vision you could use: mvision).

This creates the folder `myenv` within `~/venv`. This folder will hold all libraries you will install in future for that virtual environment.

### Activate/deactivate your virtual environment
To use your virtual environment, it needs to be activated. As long as it is activated, all `python` related activities will use libraries from this virtual environment.

Once no longer needed (or if you want to switch to another project) you have to deactivate the virtual environment.

a) To activate the virtual environment use:
```
source ~/venv/myenv/bin/activate
```
Your prompt will change to something like `(myenv)` which confirms your virtual environment is active.

b)	To deactivate your environment use:
```
(myenv) deactivate
```
Your prompt will change back to your regular prompt.

### To install a library
To install a library `my-library` run in the activated virtual environment (you can be in any folder to run this command, as long as your virtual environment is activated):
```
(myenv) python3 -m pip install my-library
```
This will install the library `my-library` in your virtual environment. It will be available as long as your virtual environment is activated.

