# jupyter-seminar

## installation

Simple instructions to start a Jupyter notebook using a virtualenv environment in Python 3.

```shell
# If pip3 is not installed, install it
sudo apt-get install python3-pip

# Upgrade
pip3 install --upgrade pip

# If virtualenv is not installed, install it
# Feel free to use either pip or pip3, doesn't matter
pip install virtualenv

# Move to the folder and create the virtualenv
virtualenv -p python3 <my-virtualenv-name>

# Activate the virtualenv
source <my-virtualenv-name>/bin/activate

# Install Jupyter
pip3 install jupyter

# Install spaCy
pip install spacy

# Install scipy, needed for some examples
pip install scipy

# Install spaCy English models
python -m spacy download en
python -m spacy download en_core_web_lg

# Run Jupyter (from withing the folder with the virtualenv folder)
jupyter notebook
```


## spaCy notebooks

Original source: https://github.com/explosion/spacy-notebooks



## spacy.displacy.serve raises TypeError

TypeError: __init__() got an unexpected keyword argument 'encoding'

Solution source: https://github.com/explosion/spaCy/issues/2810
Current workaround: 
```shell
pip install "msgpack-numpy<0.4.4.0"
```