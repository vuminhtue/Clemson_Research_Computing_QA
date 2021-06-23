---
title: "Use of R container"
teaching: 5 min
exercises: 0
questions: "How to run R container in Palmetto HPC"
objectives:
- "Download R Studio container"
- "Run RStudio GUI"
keypoints:
- "R, container"
---

## Create RStudio from docker container

Request for a compute node

```bash
mkdir ~/rstudio
cd rstudio
mkdir var
singularity build rstudio.img docker://rocker/rstudio
SINGULARITYENV_PASSWORD=abc123 SINGULARITYENV_S6_READ_ONLY_ROOT=1 singularity run -B /home/tuev/workspace/rstudio/var:/var rstudio.img
```

Use Socket Proxy forward to access the rstudio server at PALMETTO_NODE:8787

https://www.palmetto.clemson.edu/palmetto/advanced/proxy/
