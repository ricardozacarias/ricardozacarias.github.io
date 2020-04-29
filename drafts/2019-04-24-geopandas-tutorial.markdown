---
layout: post
title:  "Geopandas Tutorial"
date:   2020-05-11
categories: Python Geodata Geopandas Tutorial
permalink: /:title
---
TLDR: a short and sweet tutorial based on the content of this [post](https://ricardozacarias.com/padarias). An introduction to Geopandas, choosing the right projections and performing geometric manipulations.

<h1 id="posts-label"></h1>

You might have noticed from my previous posts that I like maps. I think there's something about squiggly lines filled with colors that reminds me of children's coloring books. 

If you want to try it out you can download the data I used here and here.

Alright so now we have the latitude and longitude coordinates for each store, let's look at them. This is where one of my favorite Python libraries comes in: [Geopandas](https://geopandas.org/).

To oversimplify it, Geopandas integrates:

- [Fiona](https://pypi.org/project/Fiona/): to read and write geographic files (shapefiles, GeoJSON);
- [Pandas](https://pandas.pydata.org/): to use the DataFrame structure and create GeoDataFrames and GeoSeries;
- [Pyproj](https://pypi.org/project/pyproj/): to perform projections of different Coordinate Reference Systems (CRS);
- Shapely: to calculate distances and geometric manipulations;
- Matplotlib: to plot maps.

Geopandas combines all these libraries into **one, awesome** geo-package.



Shapely is a BSD-licensed Python package for manipulation and analysis of planar geometric objects.

Now we need a frame of reference. To answer our question we need Lisbon map. Lisbon has a data portal where we can find the polygons that define the city and inner divisions (freguesias).

With this library we can

<i class="fas fa-camera"></i>



### Geographical Parenthesis:

Most location data is stored by default as latitude-longitude coordinates which specify every place on the surface of an ellipsoid (also known as the Earth). 

This is important because all the geometrical manipulations available in Shapely are 

This means that we need to project latitude and longitude values into a Coordinate Reference System (CRS) in 2D. 

To choose the right cartesian projection for your project you can go to [this website](https://epsg.io/) and input the region you're working on. 