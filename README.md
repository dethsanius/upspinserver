[![Build Status](https://travis-ci.org/mwuertinger/upspinserver.svg?branch=master)](https://travis-ci.org/mwuertinger/upspinserver)
# Dockerized Upspinserver
This repository contains a `Dockerfile` which allows to package `upspinserver`
in a Docker image in order to simplify distribution.

## What is Upspin?
According to the project's [documentation](https://github.com/upspin/upspin):
Upspin is an experimental project to build a framework for naming and sharing
files and other data securely, uniformly, and globally: a global name system of sorts.

## How to build
```sh
docker build -t dethsanius/upspinserver:latest .
docker push dethsanius/upspinserver:latest
```
The image is built automatically by
[TravisCI](https://travis-ci.org/mwuertinger/upspinserver) at least once a day
and the resulting images are pushed to
[Docker Hub](https://hub.docker.com/r/mwuertinger/upspinserver/).

## How to run
This configuration of `upspinserver` uses the local filesystem to store all of
its data. Therefore you need to map a local directory into the container at the
`/upspin` location.

```sh
docker run \
  -v /local/path/to/upspin:/upspin \
  -p 443:443 -p 80:80 \
  dethsanius/upspinserver:latest
```

## Kubernetes

In the Kubernetes folder you will find the files I use to host this on my Kubernetes cluster. Just apply those files in a reasonable order and you should be good. 

P.S. Right now there seems to be some jankyness with certs and with ports. None of these seem to make a real impact as of now, but wold like to fix both of these issues.