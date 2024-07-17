# Guide to Choosing a Docker Image Version

## Recommended Version

```sh
docker pull jacobkl/staticjinjaplus:0.1.1-slim
```

## Latest Default Version
Based on python:3.9-slim
```sh
docker pull jacobkl/staticjinjaplus
```
```sh
docker pull jacobkl/staticjinjaplus:latest
```

## Based on python:3.9-slim

### Latest Version on python:3.9-slim
```sh
docker pull jacobkl/staticjinjaplus:latest-slim
```

### Version 0.1.0 on python:3.9-slim
```sh
docker pull jacobkl/staticjinjaplus:0.1.0-slim
```

### Version 0.1.1 on python:3.9-slim
```sh
docker pull jacobkl/staticjinjaplus:0.1.1-slim
```

## Based on ubuntu:24.04

### Latest Version on ubuntu:24.04
```sh
docker pull jacobkl/staticjinjaplus:latest-ubuntu
```

### Version 0.1.0 on ubuntu:24.04

```sh
docker pull jacobkl/staticjinjaplus:0.1.0-ubuntu
```

### Version 0.1.1 on ubuntu:24.04

```sh
docker pull jacobkl/staticjinjaplus:0.1.1-ubuntu
```
## Run

```sh
docker run --rm -v "path/for/StaticJinjaPlus/templates:/app/templates" -v "path/for/StaticJinjaPlus/build:/app/build" your_docker_username/staticjinjaplus:<tag> -w
```

## To build and push your own image, you can use the following commands:
You can modify the Dockerfile if you need different settings.

```sh
docker build -t your_docker_username/staticjinjaplus:<tag> -f path/for/your/Dockerfile path/for/your/repository_with_Dockerfile
```
```sh
docker push your_docker_username/staticjinjaplus:<tag>
```




