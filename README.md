# Python & NLP. Introduction to spaCy with Jupyter notebooks

PyladiesBCN April 2019 meetup.

Original source: https://github.com/explosion/spacy-notebooks








## Requirements

* Python3 
* Jupyter Notebook
* spacy
* scipy
* spaCy English model: python -m spacy download en










## Installation example

For example, we can use [miniconda](https://docs.conda.io/en/latest/miniconda.html) to create an isolated Python environment that does not mess with our system Python. 

After installing miniconda, create and activate a new python 3.7 envirinment:

```shell
$ conda create -n spacy python=3.7
$ conda activate spacy
```

Let's make sure that we git everything right by checking which python are we using:

```shell
$ which python
.../miniconda3/envs/spacy/bin/python

$ python
Python 3.7.3 (default, Mar 27 2019, 16:54:48) 
[Clang 4.0.1 (tags/RELEASE_401/final)] :: Anaconda, Inc. on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

Now lets install the required packages and spaCy models in our new environment:

```shell

$ pip install jupyter
$ pip install spacy
$ pip install scipy

$ python -m spacy download en
```

Lastly, clone the repository and run jupyter notebook within the project folder:

```shell
$ git clone https://github.com/pyladies-bcn/spacy-workshop
$ cd spacy-workshop
$ jupyter notebook
```


### NotADirectoryError

There seems to be an open issue with Python 3.7 and Mac, raising the following error:

```shell
$ jupyter notebook
NotADirectoryError: [Errno 20] Not a directory: 'xdg-settings'
```

If this is the case, in https://github.com/jupyter/notebook/issues/3746 they propose this fix:

```
It's a if/else logic bug in webbrowser.py; a simple fix is to edit /usr/local/Cellar/python/3.7.0/Frameworks/Python.framework/Versions/3.7/lib/python3.7/webbrowser.py (or wherever Jupyter is pointing you to) and then look for xdg-settings in the code.

Several lines above (15 in my case), you will have if sys.platform[:3] == "win": if you change it to elif sys.platform[:3] == "win": then the Darwin/Windows/Linux will work properly. I'm running python3.7 from Homebrew using macOS 10.14.2.
```

Alternative, use this workaround and open the url manually in your browser (including the token):

```shell
$ jupyter notebook --no-browser
[I 11:51:02.843 NotebookApp] Serving notebooks from local directory: /.../spacy-workshop
[I 11:51:02.843 NotebookApp] The Jupyter Notebook is running at:
[I 11:51:02.843 NotebookApp] http://localhost:8888/?token=f592e3a9f94783dd85068edd65fd6a3246369e287df41a88
[I 11:51:02.844 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 11:51:02.849 NotebookApp] 
```


### spacy.displacy.serve raises TypeError

TypeError: __init__() got an unexpected keyword argument 'encoding'

Solution source: https://github.com/explosion/spaCy/issues/2810

Current workaround: 

```shell
pip install "msgpack-numpy<0.4.4.0"
```













## slides

[Source](https://medium.com/learning-machine-learning/present-your-data-science-projects-with-jupyter-slides-75f20735eb0f)


### Serve Locally and Iterate

```shell
jupyter nbconvert 00_jupyter_intro.ipynb --to slides --post serve --SlidesExporter.reveal_theme=serif --SlidesExporter.reveal_scroll=True --SlidesExporter.reveal_transition=none
```

Brief overview of configuration used :

- **SlidesExporter.reveal_theme**: sets the theme to serif. [https://github.com/hakimel/reveal.js/tree/master/css/theme](https://github.com/hakimel/reveal.js/tree/master/css/theme) has list of themes that ship by default with reveal.js: night, simple, sky, league, blood...
- **SlidesExporter.reveal_scroll**: sets the scrolling option to True. For big images or long cells scrolling options are helpful. It’s also helpful for visualizing dataframes.
- **SlidesExporter.reveal_transition**: Sets the transition to None. I don’t like to use any transition effect because adding them creates a sort of jerkiness to the screen which I believe to be unsuitable for code. The optins are : none, fade, slide, convex, concave and zoom.


### Generate HTML file with the slides

```shell
jupyter nbconvert 00_jupyter_intro.ipynb --to slides
```
