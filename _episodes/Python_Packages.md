---
title: "Install python packages"
teaching: 5 min
exercises: 0
questions: "How to install certain tough package in python"
objectives:

keypoints:
- "Matplotlib, Basemap, gdal, osgeo"
---

### Install matplotlib

```python
pip install -U matplotlib==3.2
```

### Install Basemap

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

### Install gdal & osgeo

```python
$ conda install -c conda-forge gdal==3.0.1
$ python
>> from osgeo import gdal
```
