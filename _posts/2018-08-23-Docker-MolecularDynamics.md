---
title: "Setting up Molecular Dynamics simulation with GPU and Docker"
date: 2018-08-23
tags: [Methods]
header:
    #image: "/assets/images/404Page.jpg"
excerpt: "Molecular Dynamics in Docker Container with GPU"

---

This post is aimed to getting stared with Docker container for Molecular Dynamics 
simulation with GPU (Cuda) computing. This is a note written for personal reference, hence not a
complete stand-alone. 

### Docker
[docker file for utility](https://github.com/taushifkhan/Docker)

## GROMACS with GPU support

Dockerfile : ./gmxDocker/Dockerfile

## Requisites
1. docker [nvidia-docker2]
2. gromacs [will use 2018v]
3. location of cuda library [for gpu utility]

## Build

1. cd gmxDocker
2. `docker build .`

Using Dockerfile , docker will go through all the instructions. Important is cuda configuration

### CUDA configuration [example]
`
ENV CUDA_HOME=/usr/local/cuda-9.0`
`ENV LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-9.0/lib64:/usr/local/cuda-9.0/lib64/stubs`
`ENV PATH=$PATH:/usr/local/cuda-9.0/bin
`

gromacs will be installed in /opt/gromacs

A successful bult will give an container id <cid>. Which will be used in further steps

## RUN

1. check build: 

We will mount a volume to the container which has the gromacs configured file (.tpr). nvidia has to be passed on runtime (see https://github.com/NVIDIA/nvidia-docker).

`docker run -v '/home/gmxDocker/TestVol:/home/gmx/' --runtime=nvidia -it <cid> /bin/bash -c 'source /opt/gromacs/bin/GMXRC ;gmx -version; ls'`

Check (for no zero value)
 * CUDA driver:        9.0 
 * CUDA runtime:       9.0
if you find these values to be unusual, check the confuguration of nvidia and cuda

2. Launch a md run

The pre compiled tpr file will be used to check the nvidia-GPU compilation

`docker run -v '/home/gmxDocker/TestVol:/home/gmx/' --runtime=nvidia -it <cid> /bin/bash -c 'source /opt/gromacs/bin/GMXRC ;gmx -version; ls; gmx mdrun -s 2Jv8_6_10ms.tpr -gpu_id 0'`



