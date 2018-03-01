# OpenGlow BSP Platform
The OpenGlow Standard is a drop-in replacement for the factory control boards in Glowforge Basic and Pro CNC lasers.
  
This is the [repo](https://code.google.com/archive/p/git-repo/) package to stackup Yocto layers for the OpenGlow Board Support Package, and is based upon `meta-freescale`.

As the Project is currently in early Alpha, and only supports the `master` branches for all upstream projects.

# Build and Install

To get the BSP you need to have `repo` installed:

## Install the `repo` utility:

```console
~$: mkdir ~/bin
~$: curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
~$: chmod a+x ~/bin/repo
~$: PATH=${PATH}:~/bin
```
Add the following to the end of ```~/.bashrc``` to permanently add ```repo``` to your path:
```console
export PATH=~/bin:$PATH
```
## Download the BSP source:

```console
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

## Build the OpenGlow Image
First time environment setup:
```console
(in openglow-bsp directory)
~$: MACHINE=openglow_std DISTRO=openglow . setup-environment openglow-image
~$: bitbake openglow
```
Subsequent builds:
```console
(in openglow-bsp directory)
~$: MACHINE=openglow_std . setup-environment openglow-image
~$: bitbake openglow
```

## To write the image to a bootable SD card:
```console
~$: cd tmp/deploy/images/openglow-std
-$: sudo zcat openglow-openglow_std.wic.gz | dd of=/dev/sdX bs=1M
```
