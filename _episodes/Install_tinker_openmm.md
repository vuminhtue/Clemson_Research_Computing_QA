https://github.com/TinkerTools/tinker-openmm

At time of writing this doc, we need to build Tinker-OpenMM against an OpenMM release from immediately prior to 4 March 2021. Therefore, I build openmm version 7.5.0 using conda environment:

conda install -c conda-forge openmm==7.5.0

Following are steps to install Tinker_OpenMM to Palmetto.
1. Request for a GPU node
2. Load these modules: anaconda3/2019.10-gcc/8.3.1 cuda/11.0.2-gcc/8.3.1 gcc/6.1.0 

3. Git clone tinker-openmm:
$ git clone https://github.com/TinkerTools/tinker.git

4. Build FFTW Fourier transform :
$ cd fftw
$ ./configure -prefix==/home/tuev/source/tinker/tinker/fftw
$ make && make install

5. Move into the top-level ~/tinker directory, and create a /build subdirectory.
$ cd ../ && mkdir build

6. Move into the new /build subdirectory, and copy source and related files via the commands:
$ cp ../source/**.f .
$ cp ../openmm/* .

7. Edit Makefile with following information: (these are applied to me with tinker home and openmm home)
TINKERDIR = /home/tuev/source/tinker/tinker
TINKER_LIBDIR = $(TINKERDIR)/lib
BINDIR = $(TINKERDIR)/bin
LINKDIR = $(TINKERDIR)

FFTWDIR = $(TINKERDIR)/fftw
FFTW_LIBDIR = -L$(FFTWDIR)/lib
FFTW_LIBS = -lfftw3_threads -lfftw3

OPENMMDIR = /home/tuev/.conda/envs/openmm750
OPENMM_INCLUDE = $(OPENMMDIR)/include
OPENMM_LIBDIR = -L$(OPENMMDIR)/lib
OPENMM_LIBS = -lOpenMM -lOpenMMAmoeba

CUDA_DIR = /software/spackages/linux-centos8-x86_64/gcc-8.3.1/cuda-11.0.2-g47zt3sfdo5camhrju5orm5pwkvjf3n2
CUDA_INCLUDE = $(CUDA_DIR)/include
CUDA_LIB = $(CUDA_DIR)/lib

# Uncomment below for 64-bit Linux
CUDA_LIB = $(CUDA_DIR)/lib64
NVML_INCLUDE = /usr/include/nvidia/gdk
NVML_LIB = /usr/local/cuda/lib64/stubs

8. Run the "make" command to build executables. When the build is finished, there will be three executables produced in the build directory:
"analyze_omm.x", "bar_omm.x" and "dynamic_omm.x".
