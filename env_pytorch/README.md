# env_setup

Environment setup guide


## Notes

Since nvidia-docker is not fully integrated with docker-compose now, you have to install docker-compose & docker-py manually

```shell
pip3 install git+https://github.com/docker/docker-py.git
pip3 install git+https://github.com/yoanisgil/compose.git@device-requests
```

## Use docker-compose to build this image locally & start server

Make sure you have **docker-compose** installed on the host.

```shell
COMPOSE_API_VERSION=auto docker-compose up -d
```

## Connect to the container

```shell
ssh -p6471 $Hostname
```
