---
title: "8/17/2020"
author: "Brian Stewart"
output: html_document
---


Importing necessary libraries for map creation.  

```r
library(leaflet)
library(dplyr)
library(htmltools)
```

Creating a data frame of the New Seven Wonders of the World and their respective latitude and longitude.  


```r
df <- data.frame(wonder = c('Great Wall of China', 'Petra', 'Colosseum', 'Chichen Itza', 'Machu Picchu', 'Taj Mahal',
                               'Christ the Redeemer'),
                    lat = c(40.4319, 30.3285, 41.8902, 20.6843, -13.1631, 27.1751, -22.9519),
                    long = c(116.5704, 35.4444, 12.4922, -88.5678, -72.5450, 78.0421, -43.2105))
```

Next is a list of icons which I downloaded from google to replace the default markers.  


```r
wonder_icons <- iconList(
        GW = makeIcon('H:/Coursera/Johns_Hopkins_Data_Course/First_Map/GWC.png', 20, 20),
        P = makeIcon('H:/Coursera/Johns_Hopkins_Data_Course/First_Map/Petra.png', 20, 20),
        C = makeIcon('H:/Coursera/Johns_Hopkins_Data_Course/First_Map/Col.png', 20, 20),
        CI = makeIcon('H:/Coursera/Johns_Hopkins_Data_Course/First_Map/CI.png', 20, 20),
        MP = makeIcon('H:/Coursera/Johns_Hopkins_Data_Course/First_Map/MP.png', 20, 20),
        TM = makeIcon('H:/Coursera/Johns_Hopkins_Data_Course/First_Map/TM.png', 20, 20),
        CR = makeIcon('H:/Coursera/Johns_Hopkins_Data_Course/First_Map/CTR.png', 20, 20)
)
```

The following is each wonder's respective wikipedia page so the user can read more about each wonder if they so choose.  


```r
wonder_sites <- c("<a href='https://en.wikipedia.org/wiki/Great_Wall_of_China'>Great Wall of China</a>", 
                  "<a href='https://en.wikipedia.org/wiki/Petra'>Petra</a>", 
                  "<a href='https://en.wikipedia.org/wiki/Colosseum'>Colosseum</a>", 
                  "<a href='https://en.wikipedia.org/wiki/Chichen_Itza'>Chichen Itza</a>", 
                  "<a href='https://en.wikipedia.org/wiki/Machu_Picchu'>Machu Picchu</a>", 
                  "<a href='https://en.wikipedia.org/wiki/Taj_Mahal'>Taj Mahal</a>",
                  "<a href='https://en.wikipedia.org/wiki/Christ_the_Redeemer_(statue)'>Christ the Redeemer</a>")
```

Lastly is the creation of the map. This map shows each wonder and its corresponding icon and if the user clicks on the icon they will get a link popup to the wikipedia page.  


```r
df %>%
        leaflet() %>%
        addTiles() %>%
        addMarkers(~long, ~lat, label = htmlEscape(df$wonder), popup = wonder_sites, icon = ~wonder_icons)
```

```
## PhantomJS not found. You can install it with webshot::install_phantomjs(). If it is installed, please make sure the phantomjs executable can be found via the PATH variable.
```

```
## Warning in normalizePath(path.expand(path), winslash, mustWork): path[1]="webshot24b4bd557b6.png": The system cannot find
## the file specified
```

```
## Warning in file(con, "rb"): cannot open file 'C:
## \Users\JASON_~1\AppData\Local\Temp\RtmpWKN6So\file24b4588b2baa\webshot24b4bd557b6.png': No such file or directory
```

```
## Error in file(con, "rb"): cannot open the connection
```

