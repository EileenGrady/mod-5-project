# Tornado Damage in the US: 2010-2018

This map was created as part of the New Maps Plus program to experiment with Mapbox GL JS. It shows tornado paths in the US from 2010 to 2018, and makes use of several examples from the Mapbox GL JS API Documentation.

1. [Create a time slider](https://docs.mapbox.com/mapbox-gl-js/example/timeline-animation/)
2. [Animate a point along a route](https://docs.mapbox.com/mapbox-gl-js/example/animate-point-along-route/)
3. [Fit to the bounds of a line string](https://docs.mapbox.com/mapbox-gl-js/example/zoomto-linestring/)
4. [Create a hover effect](https://docs.mapbox.com/mapbox-gl-js/example/hover-styles/)
5. and a variation of [Display a popup on click](https://docs.mapbox.com/mapbox-gl-js/example/popup-on-click/)

Data Source: A zipped shapefile containing tornado paths from 1950-2018 was downloaded from the [NOAA Storm Prediction Center](https://www.spc.noaa.gov/gis/svrgis/). Data was then filtered using the command line to only include tornado paths from 2010-2018, and then to filter out paths with unknown magnitudes.

`mapshaper 1950-2018-torn-aspath.shp -filter "yr==2010||yr==2011||yr==2012||yr==2013||yr==2014||yr==2015||yr==2016||yr==2017||yr==2018" -filter-fields yr,date,time,mag,inj,fat,loss,closs,slat,slon,elat,elon -o format=geojson tornadoes.json`

`mapshaper tornadoes.json -filter "mag>-1" -o format=geojson tornadoes-filtered.json`
