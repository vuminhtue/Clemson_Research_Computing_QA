---
title: "Install RAPIDS with GPU support"
teaching: 5 min
exercises: 0
questions: "How to install Rapids with GPU support to Palmetto"
objectives:

keypoints:
- "Rapids, gpu"
---


Installing RAPIDS can be a little bit tricky. So here is what I have done so far at the time of writing this note.

Request Tesla V100 node:

```bash
$ qsub -I -l select=1:ncpus=16:mpiprocs=16:mem=62gb:ngpus=2:gpu_model=v100,walltime=72:00:00
```

Load necessary modules:

```bash
$ module load anaconda3/2019.10-gcc/8.3.1  cuda/10.2.89-gcc/8.3.1
```

Follow the tutorial here:
https://rapids.ai/start.html

Here is the command to create  conda environment and install rapids that is successful for me:

```bash
$ conda create -n rapids-0.17 -c rapidsai -c nvidia -c conda-forge \
    -c defaults rapids-blazing=0.17 python=3.7
```   
