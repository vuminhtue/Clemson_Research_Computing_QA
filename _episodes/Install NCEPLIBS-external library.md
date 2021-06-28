---
title: "Install NCEPLIBS-external from github"
teaching: 5 min
exercises: 0
questions: "How to Install NCEPLIBS-external from github"
objectives:
- "Git clone NCEPLIBS-external from github"
- "Install the binary"
keypoints:
- "NCEPLIB-external"
---

## Install NCEPLIBS-external from github

Request for a compute node

```bash
$ qsub -I -l select=1:ncpus=16::mpiprocs=16:mem=32gb:interconnect=any,walltime=24:00:00
Clone particular version 1.1.0 or 1.0.0:
$ git clone -b ufs-v1.1.0 --recursive https://github.com/NOAA-EMC/NCEPLIBS-external
$ cd NCEPLIBS-external/
$ mkdir build
$ cd build/
$ module load cmake/3.17.3-gcc openmpi/4.0.3-gcc/8.3.1-ucx 
$cmake -DCMAKE_INSTALL_PREFIX=/home/$USER/NCEPLIBS-external/build -DBUILD_MPI=OFF ..
$ make -j16
```
