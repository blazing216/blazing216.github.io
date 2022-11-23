---
layout: post
title:  How to use GMT
date:   2022-11-21 21:15:00 +0100
description: GMT
tags: GMT
---

### Sample velocity at points in a given region
Use `gmtselect` to select points from `points.xy` that falls in the region defined by `-R$R -J$J`. Rectangle map regions, specified by `-Rlon1/lat1/lon2/lat2r` is also supported. 

Use `grdtrack` to sample the points.
`-Rg` seems to avoid the problem of ambigious representation of longitude 
(e.g. -180 and 360 are the same longitude)
```
gmt gmtselect -R$R -J$J points.xy | gmt grdtrack -Rg -Gvelocity.grd > sampled_vs.xy
```

### How GMT tell the inside and outside of a polygon?

### Use `gmtselect` to exclude points in an area defined by a polygon
- Use `-Fpolygonfile` to specify the polygon file
- Use `-If` to select points outside the polygon. If `-If` is not given, then `gmtselect` will select the points inside the polygon
- Use `-fg` to tell `gmtselect` that your data are geographical, in longitude and latitude, if no projection is given.
- The polygon file is a muliple-segment file. It must be in ASCII. 
It can define multiple polygons, 
but no consecutive points can be "separated by 180 degrees or more in longitude",
when lon, lat is used. 

So the command to exclude points in an area (defined by `mypolygon.xy`) is
```
# GMT5
gmt gmtselect mydata.txt -Fmypolygon.xy -fg -If > myselecteddata.txt

# GMT6
gmt select mydata.txt -Fmypolygon.xy -fg -If > myselecteddata.txt
```
The output `myselecteddata.txt` will not have points falls into the given area.


### Convert UTM coordinates to longitude and latitude
UTM in 16U to lonlat
```
gmt mapproject utm.xy -Ju+16/1:1 -C -I -F
```
lonlat to UTM in 16U
```
gmt mapproject lonlat.xy -Ju+16/1:1 -C -F
```
