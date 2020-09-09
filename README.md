# docker_service

Docker container as ssh server with NVIDIA GPU enabled

## Notes

Since nvidia-docker is not fully integrated with docker-compose now, you have to install docker-compose & docker-py manually

```shell
pip3 install git+https://github.com/docker/docker-py.git
pip3 install git+https://github.com/yoanisgil/compose.git@device-requests
```

## Build ssh enabled image

First, you need to build a ssh enabled image to launch CAAS (container as a service).

The default base image is ``jerry_zj/dev_basic_gpu``, you can edit the Dockerfile under 
``build_image`` directory to your own image.

The name of the ssh enabled image is set to ``dev_basic_gpu_server`` by default, you can name your own image by edit ``docker-compose.yml`` under ``build_image`` directory.

```shell
cd build_image
docker-compose build
```

## Use docker-compose to start a server

After the image is built, you can use the following command to start a container

In ``tvm_dev``, we mount your home directory to the container, you can specify a certain path instead.

Make sure you have **docker-compose** installed on the host.

```shell
cd tvm_dev
COMPOSE_API_VERSION=auto docker-compose up -d
```

## Connect to the container

```shell
ssh -p$SPECIFIED_PORT $Hostname
```
