# Guide to Choosing a Docker Image Version

## To build and push your own image, you can use the following commands:

You can modify the Dockerfile if you need different settings.

```sh
docker build -t your_dockerhub_username/staticjinjaplus:<tag> -f path/for/your/Dockerfile path/for/your/repository_with_Dockerfile
```
```sh
docker push your_dockerhub_username/staticjinjaplus:<tag>
```

**If you need to change the `version` and `checksum`, use:**

Get the hash-sum of the file and use it in the `CHECKSUM` field.

Example:

```sh
curl -sL https://github.com/MrDave/StaticJinjaPlus/archive/refs/tags/0.1.0.tar.gz | sha256sum
```

```sh
docker build --build-arg VERSION=<required_version> --build-arg CHECKSUM=<hash_sum> -t your_dockerhub_username/staticjinjaplus:<tag> -f path/for/your/Dockerfile .
```

## By default, images with version are built with version `0.1.1`, because the corresponding arguments are specified in the docker file.

**Example:**

```sh
docker build -t your_dockerhub_username/staticjinjaplus:0.1.1-python -f 0.1/python/Dockerfile .
```

## By default, image with all the recent changes is taken from the `main` branch

**Example:**

```sh
docker build -t your_dockerhub_username/staticjinjaplus:latest -f develop/python/Dockerfile .
```

## Build images for development:
```sh
docker build -t your_dockerhub_username/staticjinjaplus:develop -f develop/ubuntu/Dockerfile .
```
## Building a slim image for development:
```sh
docker build -t your_dockerhub_username/staticjinjaplus:develop-slim -f develop/python/Dockerfile .
```

## Build image version 0.1.0:
```sh
docker build --build-arg VERSION=0.1.0 --build-arg CHECKSUM=$(curl -sL https://github.com/MrDave/StaticJinjaPlus/archive/refs/tags/0.1.0.tar.gz | sha256sum | awk '{print $1}') -t your_dockerhub_username/staticjinjaplus:0.1.0 -f 0.1/ubuntu/Dockerfile .
```
## Build slim-image version 0.1.0:
```sh
docker build --build-arg VERSION=0.1.0 --build-arg CHECKSUM=$(curl -sL https://github.com/MrDave/StaticJinjaPlus/archive/refs/tags/0.1.0.tar.gz | sha256sum | awk '{print $1}') -t your_dockerhub_username/staticjinjaplus:0.1.0-slim -f 0.1/python/Dockerfile .
```
## Build image version 0.1.1:
```sh
docker build --build-arg VERSION=0.1.1 --build-arg CHECKSUM=$(curl -sL https://github.com/MrDave/StaticJinjaPlus/archive/refs/tags/0.1.1.tar.gz | sha256sum | awk '{print $1}') -t your_dockerhub_username/staticjinjaplus:0.1.1 -f 0.1/ubuntu/Dockerfile .
```
## Build slim-image version 0.1.1:
```sh
docker build --build-arg VERSION=0.1.1 --build-arg CHECKSUM=$(curl -sL https://github.com/MrDave/StaticJinjaPlus/archive/refs/tags/0.1.1.tar.gz | sha256sum | awk '{print $1}') -t your_dockerhub_username/staticjinjaplus:0.1.1-slim -f 0.1/python/Dockerfile .
```

## Building the latest image:
```sh
docker build --build-arg VERSION=0.1.1 --build-arg CHECKSUM=$(curl -sL https://github.com/MrDave/StaticJinjaPlus/archive/refs/tags/0.1.1.tar.gz | sha256sum | awk '{print $1}') -t your_dockerhub_username/staticjinjaplus:latest -f 0.1/ubuntu/Dockerfile .
```

## Build slim-image for the latest version:
```sh
docker build --build-arg VERSION=0.1.1 --build-arg CHECKSUM=$(curl -sL https://github.com/MrDave/StaticJinjaPlus/archive/refs/tags/0.1.1.tar.gz | sha256sum | awk '{print $1}') -t your_dockerhub_username/staticjinjaplus:slim -f 0.1/python/Dockerfile .
``` 

## Run the following commands to upload the built images to Docker Hub:

```sh
docker push your_dockerhub_username/staticjinjaplus:develop
docker push your_dockerhub_username/staticjinjaplus:develop-slim
docker push your_dockerhub_username/staticjinjaplus:0.1.0
docker push your_dockerhub_username/staticjinjaplus:0.1.0-slim
docker push your_dockerhub_username/staticjinjaplus:0.1.1
docker push your_dockerhub_username/staticjinjaplus:0.1.1-slim
docker push your_dockerhub_username/staticjinjaplus:latest
docker push your_dockerhub_username/staticjinjaplus:slim
```

## Run test

**If you want to test the collected image, run this command:**

```sh
docker run --rm -v "path/for/your/templates:/app/templates" -v "path/for/your/build:/app/build" your_dockerhub_username/staticjinjaplus:<tag> -w
```
