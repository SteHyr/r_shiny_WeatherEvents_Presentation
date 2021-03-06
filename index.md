---
title       : Exploring Weather Events
subtitle    :  
author      : Ste Hyr
job         :  
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---
 

## Overview

Extrem weather-events such as Tornados and Floods can cause human lives. With the climate change, the probability of and therefore the danger of extrem weather events increases. 

For the US, the Shiny-App on "Exploring Weather Events" allows to visuallize number, impact and location of recorded events. 

 
<div style='text-align: center;'>
    <img height='560' src='01.png' />
</div> 

--- 

## Event Explorer
   
The Event-explorer allows to select different event types, one or all years, the number of displayed events and the damage type. A short summary about the number of events and  relative/absolut caused damage provides a brief overview. 

Development over the years can be explored as animation (Play button under slider)

Example code for drawing circles in the map, using leaflet. 


```r
   map$addCircle(
      dataChunk$lat, 
      dataChunk$lng,
      dataChunk$effect,
      layerId = dataChunk$X,
      options=list(  
         stroke = FALSE, fill=TRUE, fillOpacity = .5),
      eachOptions = list(fillColor = dataChunk$eCol)) 
```

--- 

## Single Events

Clicking on an Event opens a popup with details about the Event. The Boxes are dynamicly created


```r
      # create remarks box or info, if no remarks available
      if (nchar(focusEvent$remark) > 1 ){ 
         remarksDiv <- tags$div(
            tags$h5("Remarks"),
            tags$div( 
               style="max-height:120px;max-width:300px;border:1px;overflow:auto;",
               sprintf("%s",focusEvent$remark)))
      } else { remarksDiv <- tags$h5("no Remarks available") 
      # create content box
      content <- as.character(tagList(
         tags$h5("Event Info"),
         sprintf("Weather Type: %s", focusEvent$etype ), tags$br(),
         sprintf("Fatalities: %s", focusEvent$fatalities ), tags$br(),
         sprintf("Injuries: %s",  focusEvent$injuries ), tags$br(),
         remarksDiv))
```

---  

##  Impressum

**Data** US National Weather Service [here(PDF-file)](http://www.weather.gov/)

**Layout** based on [SuperZip App](https://github.com/jcheng5/superzip) by [Joe Cheng](https://github.com/jcheng5)

[Github Code](https://github.com/SteHyr/r_shiny_WeatherEvents) with documentation

[App Link ](https://stehyr.shinyapps.io/r_shiny_WeatherEvents/)
