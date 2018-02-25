# OpenGlow BSP Platform

This is the Yocto Board Support Package for the OpenGlow Standard control board.
  
The OpenGlow Standard is a drop-in replacement for the factory control boards in Glowforge Basic and Pro CNC lasers.
  
This BSP is based upon `meta-freescale`.

As the Project is currently in early Alpha, and only supports the `master` and `master-next` branches for all upstream projects.

# Build and Install

To get the BSP you need to have `repo` installed:

## Install the `repo` utility:

```console
~$: mkdir ~/bin
~$: curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
~$: chmod a+x ~/bin/repo
~$: PATH=${PATH}:~/bin
```

## Download the BSP source:

```console
~$: PATH=${PATH}:~/bin
~$: mkdir openglow-bsp
~$: cd openglow-bsp
~$: repo init -u https://gitlab.openglow.org/openglow/openglow-bsp-platform.git -b master
~$: repo sync
```

At the end of the commands you have all meta packages you need to start work with.

## Create Cache Directories:
```console
~$ sudo mkdir -p /opt/freescale/yocto/imx
~$ sudo mkdir -p /opt/freescale/yocto/sstate-cache
~$ sudo chmod -R 777 /opt/freescale
```

## To build the OpenGlow image:

```console
~$: source ./setup-environment build
~$: bitbake openglow
```

## To write the image to a bootable SD card:
```console
~$: cd tmp/deploy/images/openglow-std
-$: sudo zcat openglow-openglow_std.wic.gz | dd of=/dev/sdX bs=1M
```
