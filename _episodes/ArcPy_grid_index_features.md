---
title: "Dividing grid into smaller boxes"
teaching: 5 min
exercises: 0
questions: "Using ArcPy to divide the shapefile into smaller boxes"
objectives:

keypoints:
- "ArcPy, ArcGIS Pro"
---

## Introduction
- Due to the restriction from NEAR portal that we cannot download the grid boxes with size bigger than 5 million sqft and the total area of all gridboxes cannot exceed 1.4 billion sqft
- Therefore, we need to divide the area of interest to smaller gridboxes.
- For example, the area of DFW can be divided to 300 small grids with size of 49 mi2 each, each of the 49 mi2 will again be divided into smaller 0.16 mi2 grid:
![image](https://user-images.githubusercontent.com/43855029/168157704-4b92eeca-fe08-412c-8c4f-64a5d1d95317.png)

## Step 1: Create the boundary
- Assuming that we have the boundary in term of lon/lat, we will need to create the shapefile for that.
- You can create the shapefile in ArcGIS or go to geojson.io and draw the polygon and modify the value:

![image](https://user-images.githubusercontent.com/43855029/168158497-74201889-6c06-4388-9504-066f111b5a8f.png)

- You can save the polygon as shapefile and open it in ArcGIS Pro

## Step 2: Split the big polygon into smaller 49mi2 grid:
- Open the ArcGIS Pro and load in the polygon
- Click on Analyses\Tools to load the ArcGIS Toolbox
- Search for Grid Index Feature Tool and set the polygon width/height to 7 mi:

![image](https://user-images.githubusercontent.com/43855029/168159153-bef31cdb-e682-43b6-8c9b-5e75b0280206.png)

- The 300 grids are generated:

![image](https://user-images.githubusercontent.com/43855029/168159310-4f7d3c45-402e-4d55-92c1-a323216008a0.png)

## Step 3: Apply the same Grid Index Feature to split 300 grids to 0.16mi2 grid
- We cannot use Grid Index Features for 300 grids, therefore, we will use ArcPy which is ArcGIS library in python
- ArcPy is only available in ArcGIS Pro but not in HPC or Macs yet.
- To use ArcPy, click on Analyses\Python\Python Notebook
- The new notebook appears and we can type in the following code:

```python

```
