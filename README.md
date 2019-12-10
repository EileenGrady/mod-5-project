# mod-5-project

first attempt pulling out all tornadoes from 2018, plan to time slide by month
`mapshaper 1950-2018-torn-aspath.shp -filter "yr==2018" -filter-fields yr,mo,date,mag,inj,fat,loss,closs,slat,slon -o format=geojson tornadoes-2018.json`

second attempt, pull out all tornadoes from 2010-2018, then filter out only those of magnitude 1-5
`mapshaper 1950-2018-torn-aspath.shp -filter "yr==2010||yr==2011||yr==2012||yr==2013||yr==2014||yr==2015||yr==2016||yr==2017||yr==2018" -filter-fields yr,mo,date,mag,inj,fat,loss,closs,slat,slon -o format=geojson tornadoes.json`

`mapshaper tornadoes.json -filter "mag>1" -o format=geojson tornadoes-1-5.json`