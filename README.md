raspbian-stretch
===================

[Raspbian](http://www.raspbian.org/) image for Docker on Raspberry Pi.
Tested on an OrangePi+2E.


Generating
----------

This image is built on a OrangePi+2E running armbian. A chroot is created using debootstrap and compressed so docker can add the root filesystem during the build process. The compression requires xz-utils (or something similar) to be installed on the build machine.  

[mkimage-raspbian.sh](https://github.com/schachr/docker-raspbian-stretch/blob/master/mkimage-raspbian.sh) is used to build and configure the chroot. This script **heavily** borrows from docker's [mkimage.sh](https://github.com/docker/docker/blob/master/contrib/mkimage.sh) script.

Building
--------
If you want to build this image yourself, run the following to generate the compressed chroot.

```bash
$ rm *.tar.xz
$ ./mkimage-raspbian.sh
```
Get some tacos.

```bash
$ docker build -t raspbianstretch .

### Automatic Build details
There is an `automatic build` dependency to the github repository https://github.com/schachr/docker-raspbian-stretch as well. The archive will receive updates on a regular basis to ensure that the image is up to date.
All you need to do is to pull it, remove the container (`docker rm`) if neccessary and restart it (`docker create/run`).
```

Running
-------
This image does not do anything fancy, but if you want to test it out, run the following:

```bash
$ docker run --name raspbian -it schachr/raspbian-stretch:latest /bin/bash
```
