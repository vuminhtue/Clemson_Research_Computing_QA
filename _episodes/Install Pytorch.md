---
title: "How to install Pytorch with GPU support"
teaching: 5 min
exercises: 0
questions: "How to install Pytorch with GPU support to Palmetto"
objectives:

keypoints:
- "pytorch, gpu"
---


## Install PyTorch with GPU

```bash
$ qsub -I -l select=1:ncpus=16:mem=20gb:ngpus=1:gpu_model=p100:interconnect=10ge,walltime=3:00:00
$ module load cuda/9.2.88-gcc/7.1.0 cudnn/7.6.5.32-9.2-linux-x64-gcc/7.1.0-cuda9_2 anaconda3/2019.10-gcc/8.3.1
$ conda create -n pytorch_env pip python=3.8.3
$ source activate pytorch_env
$ conda install pytorch torchvision cudatoolkit=9.2 -c pytorch
```
