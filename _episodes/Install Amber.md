## AMBER_GPU

1. Request a GPU node
2. Load necessary modules with cuda and anaconda:

```bash
$ module load cuda/10.2.89-gcc/8.3.1   anaconda3/2019.10-gcc/8.3.1
```

3. Modify the run_cmake file:

```bash
$ cmake $AMBER_PREFIX/amber20_src \
    -DCMAKE_INSTALL_PREFIX=$AMBER_PREFIX/amber20 \
    -DCOMPILER=GNU  \
    -DMPI=TRUE -DCUDA=TRUE -DINSTALL_TESTS=TRUE \
    -DDOWNLOAD_MINICONDA=FALSE -DMINICONDA_USE_PY3=FALSE \
    2>&1 | tee  cmake.log
```
 Once the CMakeCache file created, modify the CMakeCache to include: -luuid in the following line:

```bash
X11_SM_LIB:FILEPATH=/usr/lib64/libSM.so:-luuid
```

The execute the compiler command:

```bash
./run_cmake
make -j16
make install
```

## AMBER MPI NO GPU


1. Request a regular node with mpi processors
2. Load necessary modules with cuda and anaconda:

```bash
$ module load anaconda3/2019.10-gcc/8.3.1 cmake/3.17.3-gcc/8.3.1 openmpi/3.1.5-gcc/7.1.0-ucx gcc/7.1.0 parallel-netcdf/1.12.1-gcc/8.3.1-cuda10_2
```

3. configure and compile: 

```bash
$ ./configure -mpi gnu
$ make -j16
$ make install
```
