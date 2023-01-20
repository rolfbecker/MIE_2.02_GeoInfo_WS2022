# DRAFT!!! Assignment Geoinfo WS2022

General Idea:

Scrape time varying environmental data from a web site to generate time series of env. variables.

Example: Water Boards Emschergenossenschaft und Lippeverband 

## Periodic Web Scraping of Time Series 
* Discharge Q(t)
* Water Level W(t) 

https://howis.eglv.de/pegel/html/uebersicht_internet.php

## One Time Scraping of Master Data of Gauges ("Pegelstammdaten")

* As much as you can get! Loop over possible PIDVals and create URL for the web request dynamically.

https://howis.eglv.de/pegel/html/stammdaten_html/MO_StammdatenPegel.php?PIDVal=32

https://howis.eglv.de/pegel/html/stammdaten_html/MO_StammdatenPegel.php?PIDVal=28

Scrape master data completely and insert it into a PG table. Also download the "maps".

Discuss: Can we store the image data as a BLOB in the PG database? Does it make sense? What is the API?

## Georeference five gauge location maps 

E.g. georeference this picture of a map: https://howis.eglv.de/pegel/images/stationpics/maps/20012_stadtplan.gif

## PostgreSQL / PostGIS

Create a schema eglv. Create all tables and views in this schema. 

Add all time series of all parameters into one "long" measurement table. The primary key would be similar to (SID, TS, PARAM).

Create different views to extract one parameter, e.g. 
```
create view v_stations_w as
select s.sid, s.geom, s.name, m.param, m.val, m.units 
from meas m, stations s 
where m.sid = s.sid 
and PARAM = 'W';
```

## QGIS

Link to the database and create a dynamic map by means of the temporal controller.

For each time stamp create an image (temporal controller) (.png) and mpeg-ify it.  

## Nerds (extra, not graded)

Write a Python extension for QGIS such that, when you click on a gauge point, the time (Q? W?) series is plotted in a popup window.

Write a Python extension for QGIS which shows the official location map (img on website).

