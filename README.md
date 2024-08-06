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

## Run

**If you want to test the collected image, run this command:**

```sh
docker run --rm -v "path/for/your/templates:/app/templates" -v "path/for/your/build:/app/build" your_dockerhub_username/staticjinjaplus:<tag> -w
```
