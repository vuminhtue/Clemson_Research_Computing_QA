---
title: "Parallel with job array"
teaching: 5 min
exercises: 0
questions: "How to run parallel with job array in Palmetto"
objectives:

keypoints:
- "parallel, job array"
---


## Here is a sample of running job array in batch script:

The following example create 8 different directories then go into each directory, creating a new txt file:

```bash
#PBS -N Test_Array_Job
#PBS -l select=1:ncpus=1:mem=1gb
#PBS -l walltime=00:02:00
#PBS -j oe
#PBS -J 1-8

cd $PBS_O_WORKDIR

mkdir dir_PBS_${PBS_ARRAY_INDEX}
cd dir_PBS_${PBS_ARRAY_INDEX}
touch file${PBS_ARRAY_INDEX}.txt
```

Note: -J create an array job that drive the ${PBS_ARRAY_INDEX}
