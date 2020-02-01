# :football: NFL Play By Play Analysis :football:

## Motivation :bulb:
In this project, I will be analyzing the  NFL season play-by-play data from the last 5 years. I believe that there are several
extremely interesting insights that can be gained from this data.

## Exploratory Data Analysis
#### 1) Import the relevant data analysis and visualization package tools
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline
```

#### 2) Collect, load, merge, and clean data
I have collected my data in csv form
from [NFL Savant](http://nflsavant.com/about.php) and have loaded 2015-2019 Regular Season
Play By Play data into a merged Pandas DataFrame coined 'pbp', dropping all features with 
completely empty columns

```python
csvs = ['pbp-2019.csv', 'pbp-2018.csv','pbp-2017.csv','pbp-2016.csv','pbp-2015.csv']
pbp = pd.concat(map(pd.read_csv,csvs),ignore_index=True,sort=False)
pbp = pbp.dropna(axis=1,how='all',)
```

#### 3) Explore the data
I now need to begin getting acquainted with the data. Particularly, I want to understand details such as data types, common statistical mesaures of variables, and column names

```python
pbp.columns
pbp.info()
pbp.describe()
```

The above commands provide me with a variety of useful details. Some specific ones I felt could be useful:
1) There are 40 different features (27 int64, 11 obj, 2 float64)
2) There are 224,723 examples
3) Feature data types vary, some numeric, some categorical, some Boolean (0 or 1)

#### 4) Build Logistic Regression Model
At this point, I have analyzed the data. I am missing some key data points that may make my analysis noisy (score at each play), but as this a learning project, I am going to continue. I believe an interesting path to pursue would be a predictive analysis of the **Y**, the dependent variable "SeriesFirstDown", indicating a first down on the play. Though this is a simplified depictor of "success", I believe it is a good starting point to build one.

Particularly, I am interested in using logistic regression to predict probabilities of converting a play for a first down 'SeriesFirstDown ==1', as opposed to failing in that goal 'SeriesFirstDown==0' given **X**, a subset of features depicting the situation ('Yardline', 'Down', 'ToGo', 'TimeLeft'), as well as the features that can be chosen by a play caller ('PlayType', 'PassType', 'RushDirection', 'Formation').

## Prerequisites

#### Installing Python

Make sure that you have [Python installed](https://realpython.com/installing-python/) on your machine.

You might want to use [venv](https://docs.python.org/3/library/venv.html) standard Python library
to create virtual environments and have Python, `pip` and all dependent packages to be installed and 
served from the local project directory to avoid messing with system wide packages and their 
versions.

#### Installing Dependencies

Install all dependencies that are required for the project by running:

```bash
pip install -r requirements.txt
```

#### Launching Jupyter Locally

All demos in the project may be run directly in your browser without installing Jupyter locally. But if you want to launch [Jupyter Notebook](http://jupyter.org/) locally you may do it by running the following command from the root folder of the project:

```bash
jupyter notebook
```
After this Jupyter Notebook will be accessible by `http://localhost:8888`.

#### Launching Jupyter Remotely

Each algorithm section contains demo links to [Jupyter NBViewer](http://nbviewer.jupyter.org/). This is fast online previewer for Jupyter notebooks where you may see demo code, charts and data right in your browser without installing anything locally. In case if you want to _change_ the code and _experiment_ with demo notebook you need to launch the notebook in [Binder](https://mybinder.org/). You may do it by simply clicking the _"Execute on Binder"_ link in top right corner of the NBViewer.

![](./images/binder-button-place.png)

## Datasets

The list of datasets that is being used for Jupyter Notebook demos may be found in [data folder](data).
