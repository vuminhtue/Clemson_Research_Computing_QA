---
title: "Parallel with openmpi"
teaching: 5 min
exercises: 0
questions: "How to run parallel with openmpi in Palmetto"
objectives:

keypoints:
- "parallel, openmpi"
---


## First download and configure gnu hello

Request a compute node with 16 mpiprocs:

```bash
$ qsub -l select=1:ncpus=16:mpiprocs=16:mem=62gb:interconnect=fdr,walltime=3:00:00
```

Download and compile gnu-hello program:

```bash
$ wget https://ftp.gnu.org/gnu/hello/hello-2.10.tar.gz
$ tar -xvf hello-2.10.tar.gz
$ cd hello-2.10
$ ./configure
$ make
```

The **hello** binary file is created

## Request an openmpi modules then run using mpiexec or mpirin:

```bash
$ module load openmpi/3.1.4-gcc/8.3.1-ucx
$ mpiexec -np 16 hello
OR
$ mpirun -np 16 hello
```

```
Hello, world!
Hello, world!
Hello, world!
Hello, world!
Hello, world!
Hello, world!
Hello, world!
Hello, world!
Hello, world!
Hello, world!
Hello, world!
Hello, world!
Hello, world!
Hello, world!
Hello, world!
Hello, world!
```

