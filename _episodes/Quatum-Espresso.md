
There are only 3 GPU architecture supported: Kepler (sm35), Pascal (sm60) and Volta (sm70). Unfortunately, our latest Ampere (sm80) is not yet supported during the time of writing documentation for QE version 6.8.

We need to install QE to our own home directory and copy over to /software and correspondingly create modulefiles for each GPU.

Following are the step:



Request a k40, p100 or v100 nodes
Since QE required PGI installer. And PGI is recently merged with nvidia so we need to load nvhpc module:
$ module load nvhpc/21.2-gcc

Version 21.2 is current but we can install 21.7 if needed.

3. Download the QE 6.8 from github to your home directory and untar.

$ wget https://github.com/QEF/q-e/archive/refs/tags/qe-6.8.tar.gz

4. In the QE root directory, configure the compiler using corresponding GPU architecture:

$ ./configure --with-cuda=/software/spackages/linux-centos8-x86_64/gcc-8.3.1/nvhpc-21.2-bchgmtr57oym2ntcij3bnprt7nqpc2ju/Linux_x86_64/21.2/cuda/11.2 --with-cuda-runtime=11.2 --with-cuda-cc=35 --enable-openmp

$ make -j16 all

5. Once done, all binary are created in the bin folder in QE Root. They are ready for copying over to /software repo.

