# Yocto

> Layer containing Intel hardware support metadata [meta-intel](http://git.yoctoproject.org/cgit/cgit.cgi/meta-intel)

- [Creating a Yocto Image](http://www.digit.in/apps/creating-a-yocto-image-for-the-intel-galileo-board-using-split-layers-25901.html)

## Intel Galileo Yocto Source Code Cloning

```sh
xe1gyq@jessie:~/Galileo$ git clone git://git.yoctoproject.org/poky
Cloning into 'poky'...
remote: Counting objects: 322331, done.
remote: Compressing objects: 100% (78519/78519), done.
remote: Total 322331 (delta 238233), reused 321932 (delta 237835)
Receiving objects: 100% (322331/322331), 123.57 MiB | 611.00 KiB/s, done.
Resolving deltas: 100% (238233/238233), done.
Checking connectivity... done.
xe1gyq@jessie:~/Galileo$ cd poky
xe1gyq@jessie:~/Galileo/poky$ git checkout -b krogoth origin/krogoth
Branch krogoth set up to track remote branch krogoth from origin.
Switched to a new branch 'krogoth'
xe1gyq@jessie:~/Galileo/poky$ 
```

```sh
xe1gyq@jessie:~/Galileo/poky$ git clone git://git.yoctoproject.org/meta-intel
Cloning into 'meta-intel'...
remote: Counting objects: 12302, done.
remote: Compressing objects: 100% (3779/3779), done.
remote: Total 12302 (delta 7080), reused 12275 (delta 7053)
Receiving objects: 100% (12302/12302), 3.96 MiB | 608.00 KiB/s, done.
Resolving deltas: 100% (7080/7080), done.
Checking connectivity... done.
xe1gyq@jessie:~/Galileo/poky$ cd meta-intel/
xe1gyq@jessie:~/Galileo/poky/meta-intel$ git checkout -b krogoth origin/krogoth
Branch krogoth set up to track remote branch krogoth from origin.
Switched to a new branch 'krogoth'
xe1gyq@jessie:~/Galileo/poky/meta-intel$ 
```

## Intel Galileo Yocto Source Code Configuration

```sh
xe1gyq@jessie:~/Galileo/poky$ source oe-init-build-env
You had no conf/local.conf file. This configuration file has therefore been
created for you with some default values. You may wish to edit it to, for
example, select a different MACHINE (target hardware). See conf/local.conf
for more information as common configuration options are commented.

You had no conf/bblayers.conf file. This configuration file has therefore been
created for you with some default values. To add additional metadata layers
into your configuration please add entries to conf/bblayers.conf.

The Yocto Project has extensive documentation about OE including a reference
manual which can be found at:
    http://yoctoproject.org/documentation

For more information about OpenEmbedded see their website:
    http://www.openembedded.org/


### Shell environment set up for builds. ###

You can now run 'bitbake <target>'

Common targets are:
    core-image-minimal
    core-image-sato
    meta-toolchain
    meta-ide-support

You can also run generated qemu images with a command like 'runqemu qemux86'
```

```sh
xe1gyq@jessie:~/Galileo/poky/build$ bitbake-layers add-layer "$HOME/Galileo/poky/meta-intel"
xe1gyq@jessie:~/Galileo/poky/build$ echo 'MACHINE = "intel-quark"' >> conf/local.conf
xe1gyq@jessie:~/Galileo/poky/build$ 
```

## Intel Galileo Yocto Source Code Compilation Process

```sh
xe1gyq@jessie:~/Galileo/poky/build$ bitbake core-image-minimal
Parsing recipes: 100% |#########################################| Time: 00:01:20
Parsing of 886 .bb files complete (0 cached, 886 parsed). 1317 targets, 48 skipped, 0 masked, 0 errors.
NOTE: Resolving any missing task queue dependencies

Build Configuration:
BB_VERSION        = "1.30.0"
BUILD_SYS         = "i686-linux"
NATIVELSBSTRING   = "Debian-8.3"
TARGET_SYS        = "i586-poky-linux"
MACHINE           = "intel-quark"
DISTRO            = "poky"
DISTRO_VERSION    = "2.1"
TUNE_FEATURES     = "m32 i586-nlp"
TARGET_FPU        = ""
meta              
meta-poky         
meta-yocto-bsp    = "krogoth:8f51f6153a09f8048fb4c4ce9cf4a19655240de4"
meta-intel        = "krogoth:58b8e0f2e6c4f6566983baf4bc980a86592398ad"

NOTE: Fetching uninative binary shim from http://downloads.yoctoproject.org/releases/uninative/0.95/i686-nativesdk-libc.tar.bz2;sha256sum=5f27d7e0f4dd2ed80a7ff6a0d88af107b08e00765b31ed3aa180cc5ce15b0811
NOTE: Preparing RunQueue
NOTE: Executing SetScene Tasks
NOTE: Executing RunQueue Tasks
Currently 2 running tasks (65 of 2378):
0: libtool-native-2.4.6-r0 do_configure (pid 27070)
1: gcc-source-5.3.0-5.3.0-r0 do_fetch (pid 27129)
...
NOTE: Fetching uninative binary shim from http://downloads.yoctoproject.org/releases/uninative/0.95/i686-nativesdk-libc.tar.bz2;sha256sum=5f27d7e0f4dd2ed80a7ff6a0d88af107b08e00765b31ed3aa180cc5ce15b0811
NOTE: Preparing RunQueue
NOTE: Executing SetScene Tasks
NOTE: Executing RunQueue Tasks
NOTE: Tasks Summary: Attempted 2378 tasks of which 15 didn't need to be rerun and all succeeded.
```

## Intel Galileo Yocto Compilation Outputs

```sh
xe1gyq@jessie:~/Galileo/poky/build$ ls
bitbake.lock  cache  conf  downloads  sstate-cache  tmp
xe1gyq@jessie:~/Galileo/poky/build$ ls tmp/deploy/images/intel-quark/
bzImage
bzImage--4.4.3+git0+9ab4787fe2_076cc85486-r0-intel-quark-20160612054437.bin
bzImage-intel-quark.bin
core-image-minimal-initramfs-intel-quark-20160612054437.rootfs.cpio.gz
core-image-minimal-initramfs-intel-quark-20160612054437.rootfs.manifest
core-image-minimal-initramfs-intel-quark.cpio.gz
core-image-minimal-initramfs-intel-quark.manifest
core-image-minimal-intel-quark-20160612054437.hddimg
core-image-minimal-intel-quark-20160612054437.iso
core-image-minimal-intel-quark-20160612054437.rootfs.ext4
core-image-minimal-intel-quark-20160612054437.rootfs.manifest
core-image-minimal-intel-quark.ext4
core-image-minimal-intel-quark.hddimg
core-image-minimal-intel-quark.iso
core-image-minimal-intel-quark.manifest
gummibootia32.efi
microcode_20151106.cpio
microcode.cpio
modules--4.4.3+git0+9ab4787fe2_076cc85486-r0-intel-quark-20160612054437.tgz
modules-intel-quark.tgz
README_-_DO_NOT_DELETE_FILES_IN_THIS_DIRECTORY.txt
xe1gyq@jessie:~/Galileo/poky/build$ 
```

## Intel Galileo Yocto Image Creation

- [[meta-intel] [PATCH] mkgalileodisk.wks: WiC image for Galileo Gen 1/2](https://lists.yoctoproject.org/pipermail/meta-intel/2015-November/003642.html)

```sh
xe1gyq@jessie:~/Galileo/poky/build$ cat ../meta-intel/scripts/lib/wic/canned-wks/mkgalileodisk.wks 
```

```sh
# short-description: Create an Galileo Gen 1/2 disk image
# long-description: Creates a partitioned EFI disk image for Intel Galileo Gen 1/2,
# that the user can directly dd to boot media.

part /boot --source bootimg-efi --sourceparams="loader=gummiboot" --ondisk mmcblk0 --label msdos --active --align 1024

part / --source rootfs --ondisk mmcblk0 --fstype=ext3 --label platform --align 1024

bootloader  --timeout=0  --append="console=ttyS1,115200n8 earlycon=uart8250,mmio32,0x9000b000,115200n8 reboot=efi,warm apic=debug rw LABEL=boot debugshell=5"
```

- [meta-intel Building for Intel Quark X1000 microprocessor](https://download.ostroproject.org/releases/ostro-os/milestone/v1.0.0/sdk-data/intel-quark/layers/ostro-os/meta-intel/README)

```
xe1gyq@jessie:~/Galileo/poky/build$ wic list images
  mkgalileodisk                 		Create an Galileo Gen 1/2 disk image
  directdisk-bootloader-config  		Create a 'pcbios' direct disk image with custom bootloader config
  sdimage-bootpart              		Create SD card image with a boot partition
  mkgummidisk                   		Create an EFI disk image
  qemux86-directdisk            		Create a qemu machine 'pcbios' direct disk image
  directdisk-multi-rootfs       		Create multi rootfs image using rootfs plugin
  directdisk                    		Create a 'pcbios' direct disk image
  mkefidisk                     		Create an EFI disk image
  mkhybridiso                   		Create a hybrid ISO image
  directdisk-gpt                		Create a 'pcbios' direct disk image
```

```sh
xe1gyq@jessie:~/Galileo/poky/build$ wic create mkgalileodisk -e core-image-minimal
Checking basic build environment...
Done.

Creating image(s)...

Error: A native program parted required to build the image was not found (see details above).

Please bake it with 'bitbake parted-native' and try again.
```

```sh
xe1gyq@jessie:~/Galileo/poky/build$ bitbake parted-native
Loading cache: 100% |############################################################| ETA:  00:00:00
Loaded 1317 entries from dependency cache.
Parsing recipes: 100% |##########################################################| Time: 00:00:00
Parsing of 886 .bb files complete (885 cached, 1 parsed). 1317 targets, 48 skipped, 0 masked, 0 errors.
NOTE: Resolving any missing task queue dependencies

Build Configuration:
BB_VERSION        = "1.30.0"
BUILD_SYS         = "i686-linux"
NATIVELSBSTRING   = "universal"
TARGET_SYS        = "i586-poky-linux"
MACHINE           = "intel-quark"
DISTRO            = "poky"
DISTRO_VERSION    = "2.1"
TUNE_FEATURES     = "m32 i586-nlp"
TARGET_FPU        = ""
meta              
meta-poky         
meta-yocto-bsp    = "krogoth:8f51f6153a09f8048fb4c4ce9cf4a19655240de4"
meta-intel        = "krogoth:58b8e0f2e6c4f6566983baf4bc980a86592398ad"

NOTE: Preparing RunQueue
NOTE: Executing SetScene Tasks
NOTE: Executing RunQueue Tasks
NOTE: Tasks Summary: Attempted 114 tasks of which 105 didn't need to be rerun and all succeeded.
xe1gyq@jessie:~/Galileo/poky/build$ 
```

```sh
xe1gyq@jessie:~/Galileo/poky/build$ wic create mkgalileodisk -e core-image-minimal
Checking basic build environment...
Done.

Creating image(s)...

Info: The new image(s) can be found here:
  /var/tmp/wic/build/mkgalileodisk-201606120753-mmcblk0.direct

The following build artifacts were used to create the image(s):
  ROOTFS_DIR:                   /home/xe1gyq/Galileo/poky/build/tmp/work/intel_quark-poky-linux/core-image-minimal/1.0-r0/rootfs
  BOOTIMG_DIR:                  /home/xe1gyq/Galileo/poky/build/tmp/work/intel_quark-poky-linux/core-image-minimal/1.0-r0/core-image-minimal-1.0/hddimg
  KERNEL_DIR:                   /home/xe1gyq/Galileo/poky/build/tmp/deploy/images/intel-quark
  NATIVE_SYSROOT:               /home/xe1gyq/Galileo/poky/build/tmp/sysroots/i686-linux


The image(s) were created using OE kickstart file:
  /home/xe1gyq/Galileo/poky/meta-intel/scripts/lib/wic/canned-wks/mkgalileodisk.wks
```

```sh
dd if=/dev/zero of=/dev/sdf bs=1M count=512
../meta-intel-iot-devkit/scripts/wic_monkey create -e core-image-minimal ../meta-intel-iot-devkit/scripts/lib/image/canned-wks/iot-devkit.wks
```

## Intel Galileo Yocto Additional Package

- [Build and Deploy Yocto](http://android.serverbox.ch/?p=1273)

```sh
xe1gyq@jessie:~/Galileo/poky/build$ bitbake virtual/kernel -c menuconfig
xe1gyq@jessie:~/Galileo/poky/build$ bitbake-layers show-recipes
xe1gyq@jessie:~/Galileo/poky/build$ bitbake -c menuconfig busybox
xe1gyq@jessie:~/Galileo/poky/build$ nano conf/local.conf
CORE_IMAGE_EXTRA_INSTALL += "dropbear"
xe1gyq@jessie:~/Galileo/poky/build$ bitbake -f -c compile busybox
xe1gyq@jessie:~/Galileo/poky/build$ bitbake core-image-minimal
xe1gyq@jessie:~/Galileo/poky/build$ bitbake parted-native
xe1gyq@jessie:~/Galileo/poky/build$ wic create mkgalileodisk -e core-image-minimal
```

## Intel Galileo Yocto Kernel RT

[Galileo RT_Preempt](https://communities.intel.com/thread/48816)

```sh
xe1gyq@jessie:~/Galileo/poky$ git clone https://github.com/hambedded-linux/meta-hamradio.git
Cloning into 'meta-hamradio'...
remote: Counting objects: 69, done.
remote: Total 69 (delta 0), reused 0 (delta 0), pack-reused 69
Unpacking objects: 100% (69/69), done.
Checking connectivity... done.
xe1gyq@jessie:~/Galileo/poky$ cd build/
xe1gyq@jessie:~/Galileo/poky/build$ nano conf/bblayers.conf 
```

```sh
# POKY_BBLAYERS_CONF_VERSION is increased each time build/conf/bblayers.conf
# changes incompatibly
POKY_BBLAYERS_CONF_VERSION = "2"

BBPATH = "${TOPDIR}"
BBFILES ?= ""

BBLAYERS ?= " \
  /home/xe1gyq/Galileo/poky/meta \
  /home/xe1gyq/Galileo/poky/meta-poky \
  /home/xe1gyq/Galileo/poky/meta-yocto-bsp \
  /home/xe1gyq/Galileo/poky/meta-intel \
  /home/xe1gyq/Galileo/poky/meta-hamradio \
  "
```

```sh
```
