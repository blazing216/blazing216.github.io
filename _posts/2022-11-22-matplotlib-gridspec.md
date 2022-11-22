---
layout: post
title:  Use GridSpec to organise your figure
date:   2022-11-22 18:31:00 +0100
description: Easy configuration of multiple subplots
tags: matplotlib Python
---

Using `GridSpec` is easier to organise the subplots. It is like `psbasemap` in GMT, which gives more flexibility to set the position and organsiation of the subplots. 

```
import matplotlib.pyplot as plt
from matplotlib.gridspec import GridSpec

a4 = (8.27, 11.69)

fig = plt.figure(figsize=a4)
gs = GridSpec(1, 1, left=0.1, right=0.7, top=0.95, bottom=0.8)
ax = fig.add_subplot(gs[0,0])
```

More `GridSpec` can be added, like multiple `psbasemap` in GMT. 
`GridSpec` has one advantage over `psbasemap` when multiple subplots with similar x and y ranges are needed.
Using `GridSpec(m, n, ...)` can set up subplots.

