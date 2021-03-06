# CloudForest repository 
The CloudForest is a repository of scripts for calculation and visualisation of deforestation using Google Earth Engine (GEE), a cloud computing platform dedicated to geo-spatial analysis. 

## Contents
  - [Overview](#overview)
  - [Google Earth Engine](#google-earth-engine)
  - [Global Forest Change map](#global-forest-change-map)
  - [Scripts](#scripts)
  - [Installation](#installation)

## Overview
The scripts use [Hansen et al. (2013)](http://www.sciencemag.org/content/342/6160/850.abstract) [Global Forest Change map](http://earthenginepartners.appspot.com/science-2013-global-forest/download_v1.0.html) in conjunction with Google Earth Engine to calculate forest cover in years 2000 - 2012 for a given area. The JavaScript code is meant to be executed on GEE Playground, a web-based programming interface to the Engine. 

## Google Earth Engine
[Google Earth Engine](https://earthengine.google.org) (GEE) is a cloud computing platform dedicated to Earth Observation. Its massive data archive brings together over 40 years of historical and current Earth observation imagery and consists of petabytes of data, constantly growing as new imagery is acquired. API of the Earth Engine, provided in Python and JavaScript, allows seamless parallel computing and geospatial operation: developer for most of the time can remain blissfully unaware of underlying complexity of distributed computing, managing projections or resampling of data. 


## Global Forest Change map
Quantification of tree cover area and deforestation events from satellite imagery in a systematic way across the globe is a considerable challenge, which has been undertaken by group of prof. Hansen from Maryland University, in cooperation with Google team. The result, Global Forest Change (GFC) map, is a map product that provides estimates on forest cover in year 2000, as well as gain and loss events that happened until 2014 (as of version 1.2 of the map). The map has resolution 1296001 x 493200 pixels and a pixel size 30 metres. Since pixels are squares, a single pixel represents 30m * 30m = 900m<sup>2</sup> area. 

GFC map is composed of several bands (layers). Each layer is a separate image that represents a different piece of information. Here we will focus on four of them:
* **treecover2000**: percentage of tree cover in the pixel. In other words, each pixel has value from 0 till 100, with 0 meaning no forest at all and 100 full forest cover
* **loss**: pixel has value 1 if loss ever occurred during the study period.
* **gain**: pixel has value 1 if gain ever occurred during the study period.
* **lossyear**: value of a pixel denotes in which year loss occurred, starting with 2000. In other words, if pixel has value 5, then it means that the deforestation event occurred in 2005. 

It should be noted that Hansen et al. in their work used Food and Agriculture Organisation (UN) definition of a tree: any vegetation taller than 5 metres. In consequence, the GFC map captures as forest also any sort of plantations that happen to be taller than 5 metres. Although here we are using "trees" and "forest" interchangeably, it is important to stress that definition of "trees" does not imply ecological value. 

## Scripts

#### ecoregions.js
Calculation of forest area in 2000 and the sustained loss in 2001 - 2012 for the selected WWF ecoregion. Since the GFC map algorithm evaluates as tree any vegetation taller than 5 metres, and we were mostly interested in natural forest, we excluded from our analysis known wood fibre and oil palm plantations. 

#### grid_30km.js
Computation of global deforestation for a 30km x 30km grid cells.

## Installation
The JavaScript code is meant to be executed in [GEE Playground](https://ee-api.appspot.com/), a web-based interface to the Engine. Consequently, there is no installation step - user only needs to have access to the GEE. At the moment (late 2015) GEE is freely available after beta signup. 
