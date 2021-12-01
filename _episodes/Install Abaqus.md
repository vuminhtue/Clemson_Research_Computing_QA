---
title: "How to install Abaqus to Palmetto"
teaching: 5 min
exercises: 0
questions: "Install Abaqus to Palmetto"
objectives:

keypoints:
- "Abaqus"
---

Download Abaqus installer:
Contact Brady Banister to get the latest version of Abaqus
For past version, please find in /software/src/tuev/ABAQUS/ALL
Step to install Abaqus to util02: here is example to install version 2018

```
ssh util02
sudo su
su - spack
```

Create directory to install in /software/commercial/abaqus/2018 then go to source folder:

Create install directory

```
$ mkdir /software/commercial/abaqus/2018/SIM
```

Install Abaqus solver:

```
$ cd /software/src/tuev/ABAQUS/ALL/2018/AM_SIM_Abaqus_Extend.AllOS/2/SIMULIA_AbaqusServices/Linux64/1
```

run the file to install solver (you may need to change ksh to sh script)

```
$ ./StartTUI.sh
```

Follow the guideline on the screen
install directory: /software/commercial/abaqus/2018/SIM

Install Abaqus CAE:

```
cd /software/src/tuev/ABAQUS/ALL/2018/AM_SIM_Abaqus_Extend.AllOS/1
$ ./StartTUI.sh
```

install directory: /software/commercial/abaqus/2018/SIM/CAE

license: xxxx


#NOTE for 6.14 version. Installation from spack home: (Need to modify installer.properties to match with current system)

/software/src/tuev/ABAQUS/ALL/6.14/SIM_Abaqus.AllOS/1/lnx86_64/setup -replay /software/src/tuev/ABAQUS/ALL/6.14/SIM_Abaqus.AllOS/1/installer.properties

LICENSING Issue:

By default, the teaching license will be used. There are limited teaching licenses (4 seats) compared to research (600 seats).

In order to switch the license, one need to modify the abaqus_v6.env. The location of this file is dependent on the abaqus version:

/software/commercial/abaqus/2018/SIM/linux_a64/SMA/site/abaqus_v6.env
/software/commercial/abaqus/2020/SIM/linux_a64/SMA/site/abaqus_v6.env

Modify this abaqus_v6.env and insert at the bottom of the file, the following lines:

```
license_server_type=FLEXNET
abaquslm_license_file="xxxx"
#academic=TEACHING
academic=RESEARCH
```
