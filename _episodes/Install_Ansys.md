---
title: "How to install Ansys to Palmetto"
teaching: 5 min
exercises: 0
questions: "Install Ansys to Palmetto"
objectives:

keypoints:
- "Ansys"
---

Mount the software repo to util02: being root in util02, access /reposoftware

Download Ansys installer:
Contact Brady Banister to get the latest version of Ansys
For past version, please find in /software/src/tuev/ANSYS
Step to install Ansys to util02: here is example to install version 2019 R3

```
ssh util02
sudo su
su - spack
```

3. Create install directory

```
$ mkdir /software/commercial/ansys
```

4. Go to source files and install the modules

```
$ cd /software/src/tuev/ANSYS/ANSYS_2019_R3
```

There are 4 sub-modules to install. For Fluids, Prepost and Structures, the installation is as following:

```
$ spack load libpng/h2uzsmt (linux-centos8-x86_64 / gcc@8.3.1)
$ cd STRUCTURES_2019R3_LINX64
$ ./INSTALL -silent -install_dir /software/commercial/ansys/
$ cd ../PREPPOST_2019R3_LINX64
$ ./INSTALL -silent -install_dir /software/commercial/ansys/
$ cd ../FLUIDS_2019R3_LINX64
$ ./INSTALL -silent -install_dir /software/commercial/ansys/
```

5. Install Electroc Magnetic: This is very tough, you need to install using GUI, so you can only install to your home or scratch, then copy over to /software. Only version 2020 R2 works for CentOS8. You need to use vncserver to install. It does not install properly using regular GUI

```
cd /software/src/tuev/ANSYS/ANSYS_2020_R2/ELECTRONICS_2020R2_LINX64/Electronics_202_linx64
$ ./install
```

Note: for all Ansys version installed to software/commercial/ansys/, it will create the appropriate directory for its version like v195, v202.

The silent mode will not install license to /software/commercial/ansys/. So you have to use GUI to install FLUIDS to your home or scratch system. with following information in the license detail:

Ansys Licensing Interconnect Path 2325

FLEXlm License Path 28008
server: license4.clemson.edu

It will install a folder name share_files outside other v195, v202 folder. Copy and replace this folder to /software/commercial/ansys to make the license works across all nodes.

In the modulefiles, I have preloaded corresponding anaconda module. Without anaconda, there will be lots of issue to CentOS8 system for ansys.



For Chemkinpro, which is part of Ansys, we need to add the PATH of its to Modulefile:

```
/software/commercial/ansys/v202/reaction/chemkinpro.linuxx8664/bin/
```

Following is the command to run:

```
run_chemkin.sh Pro
```
