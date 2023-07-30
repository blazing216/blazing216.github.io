---
layout: post
title:  Tips on developing new python scripts
date:   2022-06-28 18:18:00 +0100
description: Python scripts
tags: Python
---

I need to write new python scripts once a while for research projects. Sometimes I wrote the same script more than once because I forgot where the previous script is. Sometimes I wrote a similar script because the previous script does not fits my current need completely and needs minor changes. After writing same and similar scripts for several times, I found the following way can help reduce the time of rewriting.

## Separate your scripts into reusable parts and non-resuable parts.

## Create a python library collect the resuable parts.
You can use `pip install -e .` to install this library, which will automatically add in the new files you add into the folder to the package. In this way, you don't need to include the path to the script to `PATH` or `sys.path`.

## Write the non-resuable parts (calling the resuable parts) in the scripts folder under each project.
Experimenting the workflow using jupyter notebook and then use `jupyter nbconvert --to script your.ipynb` to convert the jupyter notebook to a python script.

It is OK to run the jupyter notebook using `nbconvert` as well, but the output will not show in the terminal, which makes it difficult to track the progress.
