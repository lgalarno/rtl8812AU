# rtl8812AU

This repository contains drivers for the rtl8812AU and rtl8821AU/rtl8811AU chipsets
forked from diederikdehaas's repository

Original statement from diederikdehaas:
It started out because I found a newer driver then I found elsewhere, namely version 4.3.8.
But since then I found even newer versions released by Realtek and decided to use/update those too.
If you find a newer version then I have, I'd appreciate it if you would share it.

Currently there are the following branches, named after the initial Realtek driver version.

- [version 4.3.14-1](https://github.com/lgalarno/rtl8812AU.git)

The driver (versions) are primarily targetted at [Debian](https://www.debian.org) and [Raspbian](https://www.raspbian.org), but there is no reason to assume it won't work for other distributions.

I have currently successfully compiled the driver on Debian kernel 4.19 but the original from diederikdehaas
successfully compiled on Debian kernel 3.2, 3.16, 4.1-4.15 and on Raspbian with kernel 3.18, 4.1 and 4.4.

## DKMS
[DKMS](http://linux.dell.com/dkms/) is a system which will automatically recompile and install a kernel module when a new kernel gets installed or updated.
To make use of DKMS, install the `dkms` package, which on Debian (based) systems is done like this:
```
# apt-get install dkms
```
Where '#' denotes that it should be executed as root or with sudo, but don't type that character.

To make use of the DKMS feature with this project, do the following:
```
# DRV_NAME=rtl8812AU
# DRV_VERSION=4.3.14-1
# mkdir /usr/src/${DRV_NAME}-${DRV_VERSION}
# git clone -b driver-${DRV_VERSION} https://github.com/lgalarno/rtl8812AU.git
# cd rtl8812AU
# git archive driver-${DRV_VERSION} | tar -x -C /usr/src/${DRV_NAME}-${DRV_VERSION}
# dkms add -m ${DRV_NAME} -v ${DRV_VERSION}
# dkms build -m ${DRV_NAME} -v ${DRV_VERSION}
# dkms install -m ${DRV_NAME} -v ${DRV_VERSION}
```
If you later on want to remove it again, do the following:
```
# DRV_NAME=rtl8812AU
# DRV_VERSION=4.3.14-1
# dkms remove ${DRV_NAME}/${DRV_VERSION} --all
```
