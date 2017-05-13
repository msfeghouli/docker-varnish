# Varnish Cache Docker image with latest stable version (5.1.x) [![Build Status](https://travis-ci.org/zazukoians/docker-varnish.svg)](https://travis-ci.org/zazukoians/docker-varnish)[![](https://imagelayers.io/badge/zazukoians/varnish:latest.svg)](https://imagelayers.io/?images=zazukoians/varnish:latest 'Get your own badge on imagelayers.io')

This Docker image ships [Varnish Cache](https://www.varnish-cache.org/), a HTTP accelerator designed for content-heavy dynamic web sites as well as heavily consumed APIs by Varnish Software. It is based on [Baseimage-docker](https://github.com/phusion/baseimage-docker), which is a Docker optimized version of Ubuntu LTS.

If you have any problems with this image please report issues on Github. Pull requests are also welcome.

Varnish is pulled from the offical Ubuntu LTS package repository by varnish-cache.org. This allows us to use the latest stable version 5.1.x of Varnish Cache.

We originally planned to build it on Alpine Linux to get a smaller image but had no luck with the build process there. We might re-try that another time.

### Varnish environment variables

You can change its behaviour by changing the following environment variables:

    ENV VCL_CONFIG      /etc/varnish/default.vcl
    ENV CACHE_SIZE      256m
    ENV VARNISHD_PARAMS ""

Default parameters were taken from the [The Varnish Tutorial](https://www.varnish-cache.org/docs/4.1/index.html). The default configuration file is shipped by Varnish Cache.

### Use the pre built image

The pre built image can be downloaded using Docker.

    $ docker pull zazukoians/varnish


### Build the docker image by yourself

You can also adjust and build the image according to your needs. Just clone the repository and then execute the build command.

    $ docker build -t zazukoians/varnish .


### Start the container

    $ sudo docker run -i -d -p 80 zazukoians/varnish

Note that this alone won't be very useful as the default configuration points to a backend server on localhost port 8080. This will not work as there is no such server running in this image. Instead combine this image with an instance of an application container.

_TODO add an example_

#### Start the container and keep control
The command above starts the container and runs it in foreground. You can get a console in this image by executing

    $ docker run -ti -p 443 - zazukoians/varnish /bin/bash

