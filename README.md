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

## slides

[Source](https://medium.com/learning-machine-learning/present-your-data-science-projects-with-jupyter-slides-75f20735eb0f)

### Generate HTML file with the slides

```shell
jupyter nbconvert 00_jupyter_intro.ipynb --to slides
```

### Serve Locally and Iterate

```shell
jupyter nbconvert 00_jupyter_intro.ipynb --to slides --post serve 
--SlidesExporter.reveal_theme=serif 
--SlidesExporter.reveal_scroll=True 
--SlidesExporter.reveal_transition=none
```

Brief overview of configuration used :

- **SlidesExporter.reveal_theme**: sets the theme to serif. [https://github.com/hakimel/reveal.js/tree/master/css/theme](https://github.com/hakimel/reveal.js/tree/master/css/theme) has list of themes that ship by default with reveal.js: night, simple, sky, league, blood...
- **SlidesExporter.reveal_scroll**: sets the scrolling option to True. For big images or long cells scrolling options are helpful. It’s also helpful for visualizing dataframes.
- **SlidesExporter.reveal_transition**: Sets the transition to None. I don’t like to use any transition effect because adding them creates a sort of jerkiness to the screen which I believe to be unsuitable for code. The optins are : none, fade, slide, convex, concave and zoom.