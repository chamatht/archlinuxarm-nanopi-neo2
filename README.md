This repository can be used to create an ArchLinuxARM image for the NanoPi Neo2
board.

Modified to build a image suitable for f2fs.

Dependencies
============

- `make`
- `bsdtar` (`libarchive`)
- `python2`
- `uboot-tools`
- `sudo`
- `fdisk`
- `f2fs-tools`


Prerequisite
============

In order to build the image, you need a working ARM toolchain.

Here is a simple way to get one:

    git clone https://github.com/crosstool-ng/crosstool-ng
    cd crosstool-ng
    ./bootstrap
    ./configure --enable-local
    make
    ./ct-ng aarch64-unknown-linux-gnu
    ./ct-ng build


Preparing the files
===================

Run `make` (specifying jobs with `-jX` is supported and recommended).

This will provide:

- the ArchLinuxARM aarch64 default rootfs (`ArchLinuxARM-aarch64-latest.tar.gz`)
- an u-boot image compiled for the NanoPi Neo2 (`u-boot-sunxi-with-spl.bin`)
- a boot script (`boot.scr`) to be copied in `/boot`


Installing the distribution
===========================

Run `make install BLOCK_DEVICE=/dev/mmcblk0` with the appropriate value for
`BLOCK_DEVICE`.


Ethernet
========

In order to get ethernet working, you will need a recent kernel (>= 4.13).


Goodies
=======

If you have a serial cable and `miniterm.py` installed (`python-pyserial`),
`make serial` will open a session with the appropriate settings.


TODO
====

- upstream to ArchLinuxARM
