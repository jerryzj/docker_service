# docker_service

Docker container as ssh server with NVIDIA GPU enabled

## Package required

* NVIDIA driver (It will be installed automatically in Ubuntu 20.04 LTS)
* Docker v19.03.13
* nvidia-docker2 v2.5.0-1
* docker-compose v1.27.4

## Notes

The latest ``nvidia-docker`` is integrated with ``docker-compose`` now, make sure you install the latest version of ``nvidia-docker`` and ``docker-compose``.

To install the latest version of docker, docker-compose and nvidia-docker, make sure installing them from Docker official APT repo, Pypl, and NVIDIA APT repo respectively.

## 1. Build ssh enabled image

First, you need to build a ssh enabled image to launch CAAS (container as a service).

The default base image is ``jerry_zj/dev_basic_gpu``, you can edit the Dockerfile under 
``build_image`` directory to your own image.

The name of the ssh enabled image is set to ``dev_basic_gpu_server`` by default, you can name your own image by edit ``docker-compose.yml`` under ``build_image`` directory.

The default command will build CPU and GPU images simultaneously

```shell
cd build_image
docker-compose build
```

If you want to build image for CPU only, use

```shell
cd build_image
docker-compose build cpu
```

## 2. Use docker-compose to start a server

After the image is built, you can use the following command to start a container

In ``tvm_dev``, we will mount your home directory to the container by default, you can specify a certain path instead.

```shell
cd tvm_dev
docker-compose up -d
```

## 3. Connect to the container

Note that using the specified port in ``docker-compose.yml``

```shell
ssh -p$SPECIFIED_PORT root@$Hostname
```
