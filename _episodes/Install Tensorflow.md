
## CPU version

Tensorflow 2+ requires AVX support, which some of the older nodes don't have. 

```bash
$ qsub -I -l select=1:ncpus=16:mem=60gb:interconnect=10ge,walltime=72:00:00
$ module load anaconda3/2019.10-gcc/8.3.1
$ mkdir -p ~/software/venv
$ python3 -m venv --system-site-packages ./software/venv/tf_cpu_pip
$ source ~/software/venv/tf_cpu_pip/bin/activate
$ pip install --upgrade pip
$ pip install tensorflow==2.2
$ python3 -m ipykernel install --user --name tf_cpu_pip --display-name TensorflowCPU
```

## GPU version

```bash
$ qsub -I -l select=1:ncpus=16:mem=60gb:ngpus=2:gpu_model=k40:interconnect=10ge,walltime=72:00:00
$ module load anaconda3/2019.10-gcc/8.3.1 cuda/10.2.89-gcc/8.3.1 cudnn/8.0.0.180-10.2-linux-x64-gcc/8.3.1
$ mkdir -p ~/software/venv
$ python3 -m venv --system-site-packages ./software/venv/tf_gpu_pip
$ source ~/software/venv/tf_gpu_pip/bin/activate
$ pip install --upgrade pip
$ pip install tensorflow==2.2
$ python3 -m ipykernel install --user --name tf_gpu_pip --display-name TensorflowGPU
```


