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

### Convert UTM coordinates to longitude and latitude
UTM in 16U to lonlat
```
gmt mapproject utm.xy -Ju+16/1:1 -C -I -F
```
lonlat to UTM in 16U
```
gmt mapproject lonlat.xy -Ju+16/1:1 -C -F
```
