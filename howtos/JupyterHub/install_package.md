# Install a pip package in JupyterLab
If the pip package you wish to use is not available on any kernel, you can install it for yourslef.
For this, run in a notbebook cell this command:
```
!pip install my-package
```
This will install the package `my-package` in the kernel in which the notebook is running. The package will be only available to you and will not create any conflcits for other users.
