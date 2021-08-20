---
title: "Parallel with Julia"
teaching: 5 min
exercises: 0
questions: "How to run parallel with Julia in Palmetto"
objectives:

keypoints:
- "parallel, julia"
---



1. Request  compute node with multiple cores:

```bash
qsub -I -l select=1:ncpus=16:mem=32gb:interconnect=any,walltime=4:00:00
```

2. Load the Julia module:

```bash
$ module load julia/1.4.0-gcc/8.3.1
```

3. Set the environment variable JULIA_NUM_THREADS to the number of requested CPUs:

```bash
$ export JULIA_NUM_THREADS=8
```

4. Start Julia with -p option to specify the number of workers:

```bash
julia -p 8
```

5. Within Julia, load the Distributed package:

```bash
julia> using Distributed
```

6. Double check that the number of threads is set properly:

```bash
julia> println(Threads.nthreads())
```

7. You can use this option with ps:

```bash
ps -p <pid> -L -o pid,tid,psr,pcpu
```

where <pid> is the process ID which you can get from top or from ps -u <username>.
