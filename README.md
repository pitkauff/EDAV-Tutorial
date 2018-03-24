# Working with Location Data & ggmap

Working with geographical data can be both a blessing and a curse, so please enjoy the following tutorial on how to deal with location data and how to use ggmap to make some nice graphs. 

### Part 1: Working with Geographical Data

The main focus here will be on location data encoded as latitude, longitude. For the purpose of this tutorial, we will be working with the NYC citibike data, found [here](https://s3.amazonaws.com/tripdata/index.html). The data set for May 2015 looks as follows:

``` r
setwd("~/Desktop/Umich files/TO 414 - R/Projects/CitiBike_Group5v4")
data = read.csv("201505-citibike-tripdata.csv")
str(data)
head(data)
```
