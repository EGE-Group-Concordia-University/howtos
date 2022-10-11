# Jupyter Notebooks Version Control

## Remove tracking of notebooks outputs

Based on the answer from @dirkjot of [this StackOverflow question](https://stackoverflow.com/questions/28908319/how-to-clear-an-ipython-notebooks-output-in-all-cells-from-the-linux-terminal/).

1. In each folder where notebook outputs are not be tracked add a `.gitattributes` file with this content:
```
*.ipynb filter=strip-notebook-output  
```
These files can be part of the repository.

2. Add this filter to your local git config file `.git/config` (at the root of your local cloned repository):
```
[filter "strip-notebook-output"]
        clean = "jupyter nbconvert --ClearOutputPreprocessor.enabled=True --to=notebook --stdin --stdout --log-level=ERROR"
```
This change needs to be made after cloning the repository locally.

## Remove tracking of notebooks outputs and metadata

Based on [this blog](https://timstaley.co.uk/posts/making-git-and-jupyter-notebooks-play-nice/)

1. In each folder where notebook outputs are not be tracked add a `.gitattributes` file with this content:
```
*.ipynb filter=strip-notebook-full  
```
These files can be part of the repository.

2. Add this filter to your local git config file `.git/config` (at the root of your local cloned repository):
```
[filter "strip-notebook-full"]
        clean = "jq --indent 1 \
                '(.cells[] | select(has(\"outputs\")) | .outputs) = []  \
                | (.cells[] | select(has(\"execution_count\")) | .execution_count) = null  \
                | .cells[].metadata = {} \
                | (.metadata.papermill | select(has(\"duration\")) | .duration) = null \
                | (.metadata.papermill | select(has(\"end_time\")) | .end_time) = null \
                | (.metadata.papermill | select(has(\"start_time\")) | .start_time) = null \
                '"
        smudge = cat
        required = true
```
This change needs to be made after cloning the repository locally.

The filter removes:
* all outputs and metadata of every cells.
* the papermill information which change in each execution of the notebook in the notebook metadata.
