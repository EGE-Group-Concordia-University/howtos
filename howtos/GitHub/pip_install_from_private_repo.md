# Install a Python package with `pip` from a private GitHub Repository

## Prerequisite
You must have:
- read access to the private repository 
- set up authentication to GitHub by ssh key

## Install package with `pip` from a private repository
Consider the case of a private repository on GitHub at the location `https://github.com/org/repo`.

The command to use is:
```
pip install git+ssh://git@github.com/org/repo.git
```
where `git@github.com/org/repo.git` is almost the part you obtain when clicking on `Code>Local>SSH` in GitHub.

Note however that the `:` after `git@github.com` needs to be replaced by `/`.

It is as well possible to add it to the `requirements.txt` file like so:
```
git+ssh://git@github.com/org/repo.git
```
