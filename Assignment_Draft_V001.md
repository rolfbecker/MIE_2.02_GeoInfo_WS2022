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


## Georeference five gauge location maps 

  
