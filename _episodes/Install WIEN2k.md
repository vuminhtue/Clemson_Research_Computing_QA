---
title: "How to install WIEN2k"
teaching: 5 min
exercises: 0
questions: "How to install WIEN2k to Palmetto"
objectives:

keypoints:
- "Wien2k"
---


Wien2k is the software site license!!!

Since everyone with the source code is able to install the software, so it's best to install it to private zfs. Users will be added to zfs upon request in order to access the source code and installed directory. 

## Procedure:

- Request a 1g node with more cpus/mem
- Create the installation directory: /zfs/trangroup/WIEN2k
- Extract the source code to new directory: $ tar -xf WIEN2k_19.1.tar -C WIEN2k
- Load the necessary modules: 

```bash
$ module load anaconda3/5.1.0-gcc/8.3.1 openmpi/3.1.6-gcc openblas/0.3.10-gcc/8.3.1-openmp netlib-scalapack/2.1.0-gcc perl/5.30.1-gcc fftw/3.3.8-gcc/8.3.1-mpi
$ cd WIEN2k
$ gunzip *.gz
$  ./expand_lapw #select yes to overwrite
$ ./siteconfig_lapw # select c and Enter to continue
```

Note:

```
Select LG # LG Linux (gfortran + gcc (version 6 or higher) + OpenBlas)
Your compiler: gfortran
Your compiler: gcc
Do not chooseLIBXC and ELPA
If FFTW3 is chosen. Here is the link to it: /software/spackages/linux-centos8-x86_64/gcc-8.3.1/fftw-3.3.8-asedrswhgiddp423cywfleowerhxzq7d/
After complete with FFTW, go forward
Press "R" to choose openblas and lapack library: /software/spackages/linux-centos8-x86_64/gcc-8.3.1/openblas-0.3.10-moyer3dl6atytzcgql6stzjctfgd4auq/lib/libopenblas.so.0
Shared Memory Architecture? (N)
***************************************************************************
Do you have MPI, ScaLAPACK, ELPA, or MPI-parallel FFTW installed and intend
to run finegrained parallel?

This is useful only for BIG cases (50 atoms and more / unit cell)
and your HARDWARE has at least 16 cores (or is a cluster with Infiniband)
You need to KNOW details about your installed MPI, ELPA, and FFTW )

(y/N)# Select N for now, but we can recompile software later on and specify ELPA, FFTW if needed
```

Compile all program
perl link: /software/spackages/linux-centos8-x86_64/gcc-8.3.1/perl-5.30.1-tpesnwi24fikho3hums4qbmp6qxjntyw/bin/perl
To setup the environment for WIEN users (users must be added to trangroup), each user should execute: userconfig_lapw inside: /zfs/trangroup/WIEN2k and follow the instruction
