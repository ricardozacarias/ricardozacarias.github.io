---
layout: post
title:  "Geopandas tutorial"
date:   2019-03-23 21:03:36 +0530
categories: Python Geopandas Tutorial
permalink: /:title
---
TLDR: a short and sweet tutorial based on the content of this [post](https://ricardozacarias.com/padarias). An introduction to Geopandas, choosing the right projections and performing geometric manipulations.

<h1 id="posts-label"></h1>

Once you get a developer key, you can query the code of your city of interest in Zomato's website and then use the /Search API to grab all the restaurants that match your query (note: you can only get 20 restaurants at a time, up to 100 max). Grabbing data from Zomato is not really the scope of this article but you can find the code I used [here](github.com).

| restaurant.name                               | restaurant.latitude |      | restaurant.longitude |
| --------------------------------------------- | :-----------------: | ---- | :------------------: |
| A Padaria Portuguesa - Duque D'Ávila          |       38.735        |      |       -9.14402       |
| A Padaria Portuguesa - Camões                 |       38.7111       |      |       -9.14321       |
| A Padaria Portuguesa - Barata Salgueiro       |       38.7216       |      |       -9.14896       |
| A Padaria Portuguesa - Campo de Ourique       |       38.7184       |      |       -9.16477       |
| A Padaria Portuguesa - António Augusto Aguiar |       38.7319       |      |       -9.15185       |

Alright so now we have the latitude and longitude coordinates for each store, let's look at them. This is where one of my favorite Python libraries comes in: [Geopandas](https://geopandas.org/).

To oversimplify it, Geopandas integrates:

- [Fiona](https://pypi.org/project/Fiona/): to read and write geographic files (shapefiles, GeoJSON);
- [Pandas](https://pandas.pydata.org/): to use the DataFrame structure and create GeoDataFrames and GeoSeries;
- [Pyproj](https://pypi.org/project/pyproj/): to perform projections of different Coordinate Reference Systems (CRS);
- Shapely: to calculate distances and geometric manipulations;
- Matplotlib: to plot maps.

Geopandas combines all these libraries into one, awesome geo-package.



Shapely is a BSD-licensed Python package for manipulation and analysis of planar geometric objects.

Now we need a frame of reference. To answer our question we need Lisbon map. Lisbon has a data portal where we can find the polygons that define the city and inner divisions (freguesias).

With this library we can

<i class="fas fa-camera"></i>



### Geographical Parenthesis:

Most location data is stored by default as latitude-longitude coordinates which specify every place on the surface of an ellipsoid (also known as the Earth). 

This is important because all the geometrical manipulations available in Shapely are 

This means that we need to project latitude and longitude values into a Coordinate Reference System (CRS) in 2D. 

To choose the right cartesian projection for your project you can go to [this website](https://epsg.io/) and input the region you're working on. 