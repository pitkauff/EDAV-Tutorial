# Working with Location Data & ggmap

Working with geographical data can be both a blessing and a curse, so please enjoy the following tutorial on how to deal with location data and how to use ggmap to make some nice graphs. 

### Part 1: Working with Geographical Data

The main focus here will be on location data encoded as latitude, longitude. For the purpose of this tutorial, we will be working with the NYC citibike data, found [here](https://s3.amazonaws.com/tripdata/index.html). The data set for May 2015 looks as follows:

``` r
data = read.csv("201505-citibike-tripdata.csv")
str(data)
head(data)
```
    'data.frame':	961986 obs. of  15 variables:
     $ tripduration           : int  415 1523 642 367 2734 359 236 1991 101 1070 ...
     $ starttime              : Factor w/ 728411 levels "5/1/2015 00:00:11",..: 1 2 5 3 4 7 6 8 10 9 ...
     $ stoptime               : Factor w/ 730072 levels "5/1/2015 00:03:40",..: 4 56 12 3 144 5 2 92 1 35 ...
     $ start.station.id       : int  477 293 380 537 426 439 401 532 320 297 ...
     $ start.station.name     : Factor w/ 327 levels "1 Ave & E 15 St",..: 289 196 288 203 320 130 28 243 201 105 ...
     $ start.station.latitude : num  40.8 40.7 40.7 40.7 40.7 ...
     $ start.station.longitude: num  -74 -74 -74 -74 -74 ...
     $ end.station.id         : int  442 324 507 280 327 302 438 529 276 316 ...
     $ end.station.name       : Factor w/ 327 levels "1 Ave & E 15 St",..: 279 89 119 97 260 33 252 290 95 170 ...
     $ end.station.latitude   : num  40.7 40.7 40.7 40.7 40.7 ...
     $ end.station.longitude  : num  -74 -74 -74 -74 -74 ...
     $ bikeid                 : int  17012 17390 15003 14788 21068 17406 15005 15566 19245 18382 ...
     $ usertype               : Factor w/ 2 levels "Customer","Subscriber": 2 1 2 2 2 2 2 2 2 2 ...
     $ birth.year             : int  1981 NA 1990 1978 1956 1961 1971 1993 1958 1965 ...
     $ gender                 : int  1 0 1 1 2 1 1 1 1 1 ...

The columns we will be focusing on are the start and end station latitudes and longitudes. Luckily in our case, we have all the location data, yet sometimes we may only be given partial information. Thankfully, ggmap has a built-in function that can very easily provide coordinates for certain locations. For example, if we wish to find the coordinates of Tulsa, OK and Munich, Germany, we would do the following:

```r
library(ggmap)
city_1 = "Tulsa, OK"
geocode(city_1)
```
lon             lat
<dbl>           <dbl>
-95.99278	    36.15398	

```r
city_2 = "Munich, Germany"
geocode(city_2)
```
lon             lat
<dbl>           <dbl>
11.58198        48.13513

The function is relatively flexible. We could have also said "Tulsa, Oklahoma" or "Munich, GE". Besides for city locations, the function can also retun more specific lat/lon pair, down to specific street addresses or known locations, for example:

```r
library(ggmap)
location_1 = "one infinite loop, cupertino"
geocode(location_1)
```
lon             lat
<dbl>           <dbl>
-122.0308	    37.332		

```r
location_2 = "Columbia University"
geocode(location_2)
```
lon             lat
<dbl>           <dbl>
-73.96257	    40.80754	







