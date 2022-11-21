---
layout: post
title:  How to use GMT
date:   2022-11-21 21:15:00 +0100
description: GMT
tags: GMT
---

### Sample velocity at points in a given region
`-Rg` seems to avoid the problem of ambigious representation of longitude 
(e.g. -180 and 360 are the same longitude)
```
gmt gmtselect -R$R -J$J points.xy | \
    gmt grdtrack -Rg -Gvelocity.grd > sampled_vs.xy
```