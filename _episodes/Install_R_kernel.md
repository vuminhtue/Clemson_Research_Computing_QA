---
title: "Install R kernel to JupyterHub in Palmetto"
teaching: 5 min
exercises: 0
questions: "How to Install R kernel to JupyterHub in Palmetto"
objectives:

keypoints:
- "R, JupyterHub kernel"
---

## Create conda environment
Request a node and follow these steps:

```bash
$ module load anaconda3/2019.10-gcc/8.3.1
$ conda create -n r_env r-base=3.6.1
$ source activate r_env
> install.packages("IRkernel") #(select number like 81 for closest CRAN)
> IRkernel::installspec()
```

Open Palmetto JupyterHub either through the main page or Open OnDemand, you will see R kernel there and ready to use


