---
title: "Using Matplotlib Basemap"
teaching: 5 min
exercises: 0
questions: "Problem using matplotlib basemap in JHub"
objectives:

keypoints:
- "Matplotlib Basemap"
---

Install matplotlib

```python
pip install -U matplotlib==3.2
```

Install Basemap

```python
conda install -c anaconda basemap

#Or

pip install basemap
```

Most important: once installed, you will need to know the location of PROJ_LIB:

```
$ echo $PROJ_LIB
```

Inside Jupyter Notebook, add in this line:

```python
import os
os.environ['PROJ_LIB'] = '/home/tuev/.conda/envs/skln/share/proj'
from mpl_toolkits.basemap import Basemap
```
