# OpenGlow BSP

To get the BSP you need to have `repo` installed and use it as:

## Install the `repo` utility:

```console
$: mkdir ~/bin
$: curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
$: chmod a+x ~/bin/repo
$: PATH=${PATH}:~/bin
```

## Download the BSP source:

```console
$: PATH=${PATH}:~/bin
$: mkdir openglow-bsp
$: cd openglow-bsp
$: repo init -u http://172.17.1.11/ScottW514/openglow-bsp
$: repo sync
```

At the end of the commands you have all meta packages you need to start work with.

## To build the OpenGlow image:

```console
$: source ./setup-environment build
$: bitbake openglow
```
You can use any directory to host your build.

The source code is checked out at `openglow-bsp/sources`.
