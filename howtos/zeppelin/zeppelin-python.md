# Setup Python in Apache Zeppelin 0.10.0

Official web-site: [https://zeppelin.apache.org/docs/0.10.0/quickstart/python_with_zeppelin.html](https://zeppelin.apache.org/docs/0.10.0/quickstart/python_with_zeppelin.html)

## Setup conda

Based on instructions from [JupyterHub](https://github.com/jupyterhub/jupyterhub-the-hard-way/blob/HEAD/docs/installation-guide-hard.md)

We use `conda` to manage Python environments. We install the officially maintained `conda` packages for Ubuntu,
tin order get automatic updates with the rest of the system.

Install Anacononda public gpg key to trusted store

```
curl https://repo.anaconda.com/pkgs/misc/gpgkeys/anaconda.asc | gpg --dearmor > conda.gpg
sudo install -o root -g root -m 644 conda.gpg /etc/apt/trusted.gpg.d/
```

Add Debian repo

```
echo "deb [arch=amd64] https://repo.anaconda.com/pkgs/misc/debrepo/conda stable main" | sudo tee /etc/apt/sources.list.d/conda.list
```

Install conda

```
sudo apt update
sudo apt install conda
```

This will install conda into the folder `/opt/conda/`, with the conda command available at `/opt/conda/bin/conda`.

## Setup a Python conda environment for all users

1) Create a folder for conda envs (might exist already):
```
sudo mkdir /opt/conda/envs/
```

2) Create a conda environment for Python:
```
sudo /opt/conda/bin/conda create --prefix /opt/conda/envs/python3 python=3.7
```

## Adjust configurations in Zeppelin interpreter config file

In ```conf/interpreter.json``` provide full path to ```python``` to ```zeppelin.python```
```
"value": "/opt/conda/envs/python3/bin/python3"
```
or direclty in the Zeppelin web-app: http://localhost:8080/#/interpreter
